---
title: 'Tutorial de Docker - Parte 7: Uso de Docker Compose'
description: Se describe cómo instalar y usar Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f95a4f130e8ad662b3f0eca8f6f7d2162e2d1c7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841723"
---
# <a name="use-docker-compose"></a>Uso de Docker Compose

[Docker Compose](https://docs.docker.com/compose/) es una herramienta desarrollada para ayudar a definir y compartir aplicaciones de varios contenedores. Con Compose, puede crear un archivo YAML para definir los servicios y, con un solo comando, ponerlo todo en marcha o eliminarlo.

La *gran* ventaja de usar Compose es que puede definir la pila de la aplicación en un archivo, mantenerlo en la raíz del repositorio del proyecto (ahora tendrá control de versiones) y permitir que un tercero contribuya al proyecto. Un usuario solo tendría que clonar el repositorio e iniciar la aplicación Compose. De hecho, es posible que vea bastantes proyectos en GitHub/GitLab en los que se hace exactamente esto.

¿Cómo se empieza?

## <a name="install-docker-compose"></a>Instalación de Docker Compose

Si ha instalado Docker Desktop para Windows o Mac, ya tiene Docker Compose. Las instancias de Play-with-Docker ya tienen Docker Compose instalado. Si está en un equipo Linux, tendrá que instalar Docker Compose mediante [estas instrucciones](https://docs.docker.com/compose/install/).

Después de la instalación, debería poder ejecutar lo siguiente y ver la información de la versión.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Creación del archivo de Compose

1. En la raíz del proyecto de la aplicación, cree un archivo denominado `docker-compose.yml`.

1. En el archivo de Compose, primero se define la versión del esquema. En la mayoría de los casos, es mejor usar la última versión admitida. En la [Referencia de archivos de Compose](https://docs.docker.com/compose/compose-file/) puede consultar las versiones de esquema actuales y la matriz de compatibilidad.

    ```yaml
    version: "3.7"
    ```

1. A continuación, defina la lista de servicios (o contenedores) que quiera ejecutar como parte de la aplicación.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Y ahora, comenzará a migrar un servicio cada vez al archivo de Compose.

## <a name="define-the-app-service"></a>Definición de App Service

Recuerde que este es el comando que ha usado para definir el contenedor de la aplicación (reemplace los caracteres ` \ ` por `` ` `` en Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. En primer lugar, defina la entrada del servicio y la imagen del contenedor. Puede elegir cualquier nombre para el servicio. El nombre se convertirá automáticamente en un alias de red, que será útil al definir el servicio MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Normalmente, verá el comando cerca de la definición de `image`, aunque no hay ningún requisito en la ordenación. Por tanto, continúe y muévalo al archivo.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Para migrar el elemento `-p 3000:3000` del comando, defina el valor `ports` para el servicio. Aquí usará la [sintaxis abreviada](https://docs.docker.com/compose/compose-file/#short-syntax-1), pero también hay disponible una [sintaxis larga](https://docs.docker.com/compose/compose-file/#long-syntax-1) más detallada.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Después, migre el directorio de trabajo (`-w /app`) y la asignación de volúmenes (`-v ${PWD}:/app`) mediante las definiciones de `working_dir` y `volumes`. Los volúmenes también tienen una sintaxis [abreviada](https://docs.docker.com/compose/compose-file/#short-syntax-3) y una [larga](https://docs.docker.com/compose/compose-file/#long-syntax-3).

   Una ventaja de las definiciones de volúmenes de Docker Compose es que se pueden usar rutas de acceso relativas al directorio actual.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Por último, migre las definiciones de variables de entorno con la clave `environment`.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definición del servicio MySQL

Ahora, es el momento de definir el servicio MySQL. El comando que ha usado para ese contenedor era el siguiente (reemplace los caracteres ` \ ` por `` ` `` en Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. En primer lugar, defina el nuevo servicio y asígnele el nombre `mysql` para que obtenga automáticamente el alias de red. Especifique también la imagen que se debe usar.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. A continuación, defina la asignación de volúmenes. Cuando ha ejecutado el contenedor con `docker run`, se ha creado automáticamente el volumen con nombre. Pero esto no sucede cuando se ejecuta con Compose. Tendrá que definir el volumen en la sección `volumes:` de nivel superior y, después, especificar el punto de montaje en la configuración del servicio. Para que se usen las opciones predeterminadas, solo tiene que proporcionar el nombre del volumen. Pero hay [muchas más opciones disponibles](https://docs.docker.com/compose/compose-file/#volume-configuration-reference).

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Por último, solo tiene que especificar las variables de entorno.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

En este momento, el archivo `docker-compose.yml` completo debe tener este aspecto:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Ejecución de la pila de la aplicación.

Ahora que tiene el archivo `docker-compose.yml`, puede iniciarlo.

1. En primer lugar, asegúrese de que no haya otras copias de la aplicación y la base de datos en ejecución (`docker ps` y `docker rm -f <ids>`).

1. Use el comando `docker-compose up` para iniciar la pila de la aplicación. Agregue la marca `-d` para ejecutar todo en segundo plano. Como alternativa, puede hacer clic con el botón derecho en el archivo de Compose y seleccionar la opción **Compose Up** (Activar) para la barra lateral de VS Code. 

    ```bash
    docker-compose up -d
    ```

    Cuando lo ejecute, la salida debería ser parecida a la siguiente:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Observará que el volumen se ha creado, y también una red. De forma predeterminada, Docker Compose crea automáticamente una red específica para la pila de la aplicación (motivo por el que no ha definido una en el archivo de Compose).

1. Examine los registros con el comando `docker-compose logs -f`. Verá los registros de cada uno de los servicios intercalados en una única secuencia. Esto es increíblemente útil cuando quiere comprobar si hay problemas relacionados con el control de tiempo. La marca `-f` "sigue" el registro, por lo que le proporcionará una salida en directo a medida que se genera.

    Verá una salida similar a la siguiente:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    El nombre del servicio se muestra al principio de la línea (a menudo en color) para ayudar a distinguir los mensajes. Si quiere ver los registros de un servicio específico, puede agregar el nombre del servicio al final del comando logs (por ejemplo, `docker-compose logs -f app`).

    > [!TIP]
    > **Espera por la base de datos antes de iniciar la aplicación** Cuando la aplicación se está iniciando, realmente espera a que MySQL esté en funcionamiento antes de intentar conectarse a él. Docker no tiene compatibilidad integrada para esperar a que otro contenedor esté totalmente activo, en ejecución y listo antes de iniciar otro distinto. Para los proyectos basados en Node, puede usar la dependencia [wait-port](https://github.com/dwmkerr/wait-port). Existen proyectos similares para otros lenguajes o marcos.

1. En este punto, debería poder abrir la aplicación y verla en ejecución. Y, sobre todo, lo ha hecho con un solo comando.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Visualización de la pila de la aplicación en la extensión de Docker

Si examina la extensión de Docker, puede cambiar las opciones de agrupación mediante "cog" y "group by". En este caso, quiere ver los contenedores agrupados por nombre de proyecto de Compose:

![Extensión VS con Compose](media/vs-app-project-collapsed.png)

Si examina la red, verá los dos contenedores que ha definido en el archivo de Compose.

![Extensión VS con Compose expandido](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Eliminación completa

Cuando esté listo para eliminarlo todo, simplemente ejecute `docker-compose down`, o bien haga clic con el botón derecho en la aplicación en la lista contenedores de la extensión Docker de VS Code y seleccione **Compose Down** (Anular). Los contenedores se detendrán y la red se quitará.

> [!WARNING]
> **Eliminación de volúmenes** De forma predeterminada, los volúmenes con nombre del archivo de Compose no se quitan al ejecutar `docker-compose down`. Si quiere quitar los volúmenes, tendrá que agregar la marca `--volumes`.

Después de anularlo, puede cambiar a otro proyecto, ejecutar `docker-compose up` y estar listo para contribuir a ese proyecto. Realmente es así de sencillo.

## <a name="recap"></a>Resumen

En esta sección, ha obtenido información sobre Docker Compose y cómo ayuda a simplificar drásticamente la definición y el uso compartido de aplicaciones de varios servicios. Ha creado un archivo de Compose mediante la conversión de los comandos que usaba al formato de Compose adecuado.

Llegado a este punto, comienza la finalización del tutorial. Pero se describirán algunos procedimientos recomendados sobre la creación de imágenes, ya que hay un gran problema con el Dockerfile que ha usado. Por tanto, adelante.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Procedimientos recomendados para la creación de imágenes](image-building-best-practices.md)
