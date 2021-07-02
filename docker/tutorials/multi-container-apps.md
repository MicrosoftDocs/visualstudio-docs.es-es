---
title: 'Tutorial de Docker - Parte 6: Aplicaciones de varios contenedores'
description: Procedimiento para configurar redes entre contenedores y agregar un contenedor para una base de datos MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d23d1f5d94729741630ee76263fd5b32041e9cfd
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222921"
---
# <a name="multi-container-apps"></a>Aplicaciones de varios contenedores

Hasta el momento, ha trabajado con aplicaciones de un solo contenedor. Pero ahora agregará MySQL a la pila de la aplicación. A menudo surge la siguiente pregunta: "¿Dónde se ejecutará MySQL? ¿Se instala en el mismo contenedor o se ejecuta por separado?" En general, **cada contenedor debe hacer una cosa y hacerla bien.** Algunos motivos:

- Hay una buena oportunidad de escalar las API y los front-end de forma distinta a las bases de datos.
- Los contenedores independientes permiten la versión y la actualización de las versiones de forma aislada
- Aunque puede usar un contenedor para la base de datos de forma local, es posible que quiera usar un servicio administrado para la base de datos en producción. No le interesa enviar el motor de base de datos con la aplicación después.
- La ejecución de varios procesos requerirá un administrador de procesos (el contenedor solo inicia un proceso), lo que agrega complejidad al inicio o apagado del contenedor.

Y hay más motivos. Por tanto, actualizará la aplicación para que funcione de la siguiente manera:

![Aplicación de tareas pendientes conectada al contenedor de MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Redes de contenedores

Recuerde que, de forma predeterminada, los contenedores se ejecutan de forma aislada y no saben nada sobre otros procesos o contenedores en el mismo equipo. Por tanto, ¿cómo permite que un contenedor se comunique con otro? La respuesta son las **redes**. Pero no es necesario ser un ingeniero de redes (qué alivio). Simplemente recuerde esta regla...

> [!NOTE]
> Si dos contenedores están en la misma red, pueden comunicarse entre sí. Si no lo están, no pueden.

## <a name="start-mysql"></a>Inicie MySQL

Hay dos maneras de colocar un contenedor en una red: asignarlo al inicio o conectar un contenedor existente. Por ahora, creará la red primero y adjuntará el contenedor de MySQL al inicio.

1. Cree la red.

    ```bash
    docker network create todo-app
    ```

1. Inicie un contenedor de MySQL y asócielo a la red. También definirá algunas variables de entorno que la base de datos usará para inicializar la base de datos (vea la sección "Variables de entorno" en la [lista de MySQL Docker Hub](https://hub.docker.com/_/mysql/)) (reemplace los caracteres ` \ ` por `` ` `` en Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    También verá que se ha especificado la marca `--network-alias`. Volverá a eso en breve.

    > [!TIP]
    > Observará que aquí se usa un nombre de volumen `todo-mysql-data` y se monta en `/var/lib/mysql`, que es donde MySQL almacena sus datos. Pero nunca ha ejecutado un comando `docker volume create`. Docker reconoce que quiere usar un volumen con nombre y crea uno de forma automática.

1. Para confirmar que la base de datos está en funcionamiento, conéctese a ella y compruebe que se conecta.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Cuando aparezca la solicitud de contraseña, escriba **secret**. En el shell de MySQL, enumere las bases de datos y compruebe que ve `todos`.

    ```cli
    mysql> SHOW DATABASES;
    ```

    Debería aparecer un resultado como el siguiente:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Enhorabuena. Tiene la base de datos `todos` y está lista para usarla.

## <a name="connect-to-mysql"></a>Conectarse a MySQL

Ahora que ya sabe que MySQL está en funcionamiento, ya lo puede usar. ¿Pero cómo? Si ejecuta otro contenedor en la misma red, ¿cómo encuentra el contenedor (recuerde que cada uno tiene su propia dirección IP)?

Para averiguarlo, va a usar el contenedor [nicolaka/netshoot](https://github.com/nicolaka/netshoot), que se incluye con *multitud* de herramientas que son útiles para solucionar o depurar problemas de red.

1. Inicie un contenedor nuevo mediante la imagen `nicolaka/netshoot`. Asegúrese de conectarla a la misma red.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Dentro del contenedor, use el comando `dig`, que es una herramienta de DNS útil. Busque la dirección IP del nombre de host `mysql`.

    ```bash
    dig mysql
    ```

    Verá una salida similar a esta...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    En "ANSWER SECTION," (Sección de respuesta), verá un registro `A` para `mysql` que se resuelve en `172.23.0.2` (la dirección IP probablemente tendrá otro valor). Aunque `mysql` normalmente no es un nombre de host válido, Docker ha podido resolverlo en la dirección IP del contenedor que tenía ese alias de red (¿recuerda la marca `--network-alias` que ha usado antes?).

    Esto significa que la aplicación solo tiene que conectarse a un host denominado `mysql` y se comunicará con la base de datos. Realmente es así de sencillo.

## <a name="run-your-app-with-mysql"></a>Ejecución de la aplicación con MySQL

La aplicación de tareas pendientes admite la configuración de algunas variables de entorno para especificar la configuración de conexión de MySQL. Son las siguientes:

- `MYSQL_HOST`: el nombre de host para el servidor MySQL en ejecución
- `MYSQL_USER`: el nombre de usuario para la conexión.
- `MYSQL_PASSWORD`: la contraseña para la conexión.
- `MYSQL_DB`: la base de datos que se va a usar después de establecer la conexión.

> [!WARNING]
> **Establecimiento de la configuración de conexión a través de variables de entorno** Aunque el uso de variables de entorno para establecer la configuración de conexión suele ser correcta para el desarrollo, se desaconseja encarecidamente al ejecutar aplicaciones en producción. Para entender los motivos, vea [Por qué no se deben usar variables de entorno para datos secretos](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Un mecanismo más seguro consiste en usar la compatibilidad con secretos que proporciona el marco de orquestación de contenedores. En la mayoría de los casos, estos secretos se montan como archivos en el contenedor en ejecución. Verá que muchas aplicaciones (incluida la imagen de MySQL y la aplicación de tareas pendientes) también admiten variables de entorno con un sufijo `_FILE` para apuntar a un archivo que contiene el archivo.
> Por ejemplo, si se establece la variable `MYSQL_PASSWORD_FILE`, la aplicación usará el contenido del archivo al que se hace referencia como contraseña de la conexión. Docker no hace nada para admitir estas variables de entorno. La aplicación tendrá que saber que debe buscar la variable y obtener el contenido del archivo.

Con todo lo explicado, inicie el contenedor listo para el desarrollo.

1. Especifique cada una de las variables de entorno anteriores y conecte el contenedor a la red de la aplicación (reemplace los caracteres ` \ ` por `` ` `` en Windows PowerShell).

    ```bash hl_lines="3 4 5 6 7"
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

1. Si examina los registros del contenedor (`docker logs <container-id>`), debería ver un mensaje que indica que usa la base de datos MySQL.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Abra la aplicación en el explorador y agregue algunos elementos a la lista de tareas pendientes.

1. Conéctese a la base de datos MySQL y compruebe que los elementos se escriben en la base de datos. Recuerde que la contraseña es **secret**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    En el shell de MySQL, ejecute lo siguiente:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Obviamente, la tabla tendrá un aspecto diferente porque tiene elementos propios. Pero debería ver que se almacenan allí.

Si echa un vistazo rápido a la extensión Docker, verá que tiene dos contenedores de aplicaciones en ejecución. Pero no hay ninguna indicación real de que estén agrupados en una sola aplicación. Verá cómo mejorarlo en breve.

![Extensión Docker en la que se muestran dos contenedores de aplicaciones sin agrupar](media/vs-multi-container-app.png)

## <a name="recap"></a>Resumen

En este momento, tiene una aplicación que ahora almacena sus datos en una base de datos externa que se ejecuta en un contenedor independiente. Ha obtenido información sobre las redes de contenedores y ha visto cómo se puede realizar la detección de servicios mediante DNS.

Pero es muy probable que se empiece a sentir algo abrumado con todo lo que tiene hacer para iniciar esta aplicación. Tiene que crear una red, iniciar contenedores, especificar todas las variables de entorno, exponer puertos y mucho más. Hay mucho que recordar y sin duda es complicado pasarlo a otros usuarios.

En la sección siguiente se describirá Docker Compose. Con Docker Compose, puede compartir las pilas de aplicaciones de una manera mucho más sencilla y permitir que otros las activen con un único y sencillo comando.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Uso de Docker Compose](use-docker-compose.md)
