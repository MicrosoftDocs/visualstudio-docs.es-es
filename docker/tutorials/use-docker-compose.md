---
title: 'Tutorial de Docker: parte 7: uso de Docker Compose'
description: Describe cómo instalar y utilizar Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176795"
---
# <a name="use-docker-compose"></a>Uso de Docker Compose

[Docker Compose](https://docs.docker.com/compose/) es una herramienta desarrollada para ayudar a definir y compartir aplicaciones de varios contenedores. Con Compose, puede crear un archivo YAML para definir los servicios y con un solo comando, puede hacer todo lo posible o recortarlo todo.

La *gran* ventaja de usar Compose es que puede definir la pila de la aplicación en un archivo, mantenerla en la raíz del repositorio del proyecto (ahora está controlada por la versión) y permitir que otra persona contribuya a su proyecto. Alguien solo necesitaría clonar el repositorio e iniciar la aplicación Compose. De hecho, es posible que vea bastantes proyectos en GitHub/GitLab haciendo exactamente esto ahora.

¿Cómo comenzar?

## <a name="install-docker-compose"></a>Instalación de Docker Compose

Si instaló el escritorio de Docker para Windows o Mac, ya tiene Docker Compose. Las instancias de play-with-Docker ya tienen Docker Compose instaladas. Si está en un equipo Linux, tendrá que instalar Docker Compose siguiendo estas [instrucciones](https://docs.docker.com/compose/install/).

Después de la instalación, debería poder ejecutar lo siguiente y ver la información de versión.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Crear el archivo de Compose

1. En la raíz del proyecto de la aplicación, cree un archivo denominado `docker-compose.yml` .

1. En el archivo de Compose, comenzaremos por definir la versión del esquema. En la mayoría de los casos, es mejor usar la última versión admitida. Puede consultar la referencia del [archivo de Compose](https://docs.docker.com/compose/compose-file/) para las versiones de esquema actuales y la matriz de compatibilidad.

    ```yaml
    version: "3.7"
    ```

1. A continuación, defina la lista de servicios (o contenedores) que desea ejecutar como parte de la aplicación.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Y ahora, comenzará a migrar un servicio cada vez en el archivo de Compose.

## <a name="define-the-app-service"></a>Definir el App Service

Recuerde que este es el comando que usó para definir el contenedor de la aplicación (Reemplace los ` \ ` caracteres por `` ` `` en Windows PowerShell).

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

1. Normalmente, verá el comando cerca de la `image` definición, aunque no hay ningún requisito en la ordenación. Por lo tanto, continúe y muévalo al archivo.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Migre la `-p 3000:3000` parte del comando definiendo `ports` para el servicio. Aquí usará la [Sintaxis abreviada](https://docs.docker.com/compose/compose-file/#short-syntax-1) , pero también hay una [Sintaxis](https://docs.docker.com/compose/compose-file/#long-syntax-1) más detallada disponible.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. A continuación, migre el directorio de trabajo ( `-w /app` ) y la asignación de volumen ( `-v ${PWD}:/app` ) mediante las `working_dir` definiciones de y `volumes` . Los volúmenes también tienen una sintaxis [corta](https://docs.docker.com/compose/compose-file/#short-syntax-3) y [larga](https://docs.docker.com/compose/compose-file/#long-syntax-3) .

   Una ventaja de Docker Compose definiciones de volúmenes es que se pueden usar rutas de acceso relativas desde el directorio actual.

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

1. Por último, migre las definiciones de variables de entorno mediante la `environment` clave.

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

### <a name="define-the-mysql-service"></a>Definir el servicio MySQL

Ahora, es el momento de definir el servicio MySQL. El comando que usó para ese contenedor era el siguiente (Reemplace los ` \ ` caracteres por `` ` `` en Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. En primer lugar, defina el nuevo servicio y asígnele el nombre `mysql` para que obtenga automáticamente el alias de red. Especifique también la imagen que se va a usar.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. A continuación, defina la asignación de volumen. Al ejecutar el contenedor con `docker run` , se crea automáticamente el volumen con nombre. Sin embargo, esto no sucede cuando se ejecuta con Compose. Debe definir el volumen en la sección de nivel superior `volumes:` y, a continuación, especificar el punto de montaje en la configuración del servicio. Simplemente proporcionando solo el nombre del volumen, se usan las opciones predeterminadas. Sin embargo, hay [muchas más opciones disponibles](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) .

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

En este punto, el completo `docker-compose.yml` debe tener el siguiente aspecto:

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

## <a name="run-the-application-stack"></a>Ejecutar la pila de la aplicación

Ahora que tiene el `docker-compose.yml` archivo, puede iniciarlo.

1. En primer lugar, asegúrese de que no haya otras copias de la aplicación y la base de datos en ejecución ( `docker ps` y `docker rm -f <ids>` ).

1. Inicie la pila de aplicaciones con el `docker-compose up` comando. Agregue la `-d` marca para ejecutar todo en segundo plano. Como alternativa, puede hacer clic con el botón derecho en el archivo de Compose y seleccionar la opción de **redacción** para la barra lateral de vs Code. 

    ```bash
    docker-compose up -d
    ```

    Al ejecutarlo, debería ver una salida similar a la siguiente:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Observará que el volumen se ha creado, así como una red. De forma predeterminada, Docker Compose crea automáticamente una red específica para la pila de aplicaciones (por lo que no definió una en el archivo de Compose).

1. Examine los registros con el `docker-compose logs -f` comando. Verá los registros de cada uno de los servicios intercalados en una única secuencia. Esto es increíblemente útil cuando desea ver si hay problemas relacionados con el control de tiempo. La `-f` marca "sigue" el registro, por lo que le proporcionará una salida en directo a medida que se genera.

    Si aún no lo está, verá un resultado similar al siguiente:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    El nombre del servicio se muestra al principio de la línea (a menudo coloreado) para ayudar a distinguir los mensajes. Si desea ver los registros de un servicio específico, puede Agregar el nombre del servicio al final del comando registros (por ejemplo, `docker-compose logs -f app` ).

    > [!TIP]
    > **Esperando la base de la BD antes de iniciar la aplicación** Cuando la aplicación se está iniciando, realmente se encuentra y espera a que MySQL esté en funcionamiento antes de intentar conectarse a it.DocKer no tiene ninguna compatibilidad integrada para esperar a que otro contenedor esté totalmente activo, en ejecución y listo antes de iniciar otro contenedor. En el caso de los proyectos basados en nodos, puede usar la dependencia del [Puerto de espera](https://github.com/dwmkerr/wait-port) . Existen proyectos similares para otros lenguajes o marcos de trabajo.

1. En este punto, debería poder abrir la aplicación y verla en ejecución. Y ¡ Hola! Está a un solo comando.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Ver la pila de aplicaciones en la extensión de Docker

Si observa la extensión de Docker, puede cambiar las opciones de agrupación mediante "engranaje" y "Group by". En esta instancia, desea ver los contenedores agrupados por nombre de proyecto de redacción:

![VS extension con Compose](media/vs-app-project-collapsed.png)

Si gira hacia abajo la red, verá los dos contenedores que definió en el archivo de Compose.

![Extensión de VS con redacción expandida](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Desgarrar todo

Cuando esté listo para desactivarlo, solo tiene que ejecutar `docker-compose down` o hacer clic con el botón derecho en la aplicación en la lista de contenedores en la vs Code extensión de Docker y seleccionar **componer**. Los contenedores se detendrán y se quitará la red.

> [!WARNING]
> **Quitar volúmenes** De forma predeterminada, los volúmenes con nombre en el archivo de Compose no se quitan cuando se ejecuta `docker-compose down` . Si desea quitar los volúmenes, tendrá que agregar la `--volumes` marca.

Una vez desactivado, puede cambiar a otro proyecto, ejecutar `docker-compose up` y estar listo para contribuir a ese proyecto. Realmente no es mucho más sencillo que eso.

## <a name="recap"></a>Resumen

En esta sección, ha aprendido sobre Docker Compose y cómo ayuda a simplificar drásticamente la definición y el uso compartido de aplicaciones de varios servicios. Ha creado un archivo de Compose mediante la traducción de los comandos que estaba usando en el formato de redacción adecuado.

Llegados a este punto, va a comenzar a resumir el tutorial. Sin embargo, hay algunas prácticas recomendadas sobre la creación de imágenes que se van a cubrir, ya que hay un gran problema con el Dockerfile que ha estado usando. Por lo tanto, echemos un vistazo.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Procedimientos recomendados para la creación de imágenes](image-building-best-practices.md)
