---
title: 'Tutorial de Docker, parte 6: aplicaciones de varios contenedores'
description: Cómo configurar redes entre contenedores y agregar un contenedor para una base de datos MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176801"
---
# <a name="multi-container-apps"></a>Aplicaciones de varios contenedores

Hasta este momento, ha estado trabajando con aplicaciones de contenedor único. Sin embargo, ahora agregará MySQL a la pila de la aplicación. A menudo surge la siguiente pregunta: "¿Dónde se ejecutará MySQL? ¿Se instala en el mismo contenedor o se ejecuta por separado? " En general, **cada contenedor debe hacer una cosa y hacerlo bien.** Algunos motivos:

- Hay una buena oportunidad de escalar las API y los servidores front-end de forma distinta a las bases de datos.
- Los contenedores independientes permiten la versión y la actualización de las versiones de forma aislada
- Aunque puede usar un contenedor para la base de datos localmente, puede que desee usar un servicio administrado para la base de datos en producción. No desea enviar el motor de base de datos con la aplicación después.
- La ejecución de varios procesos requerirá un administrador de procesos (el contenedor solo inicia un proceso), lo que agrega complejidad al inicio o apagado del contenedor.

Y hay más motivos. Por lo tanto, actualizará la aplicación para que funcione de la siguiente manera:

![Aplicación todo conectada al contenedor MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Redes de contenedores

Recuerde que, de forma predeterminada, los contenedores se ejecutan de forma aislada y no saben nada sobre otros procesos o contenedores en el mismo equipo. Por lo tanto, ¿cómo permite que un contenedor se comunique con otro? La respuesta es la **red**. Ahora no tiene que ser un ingeniero de red (alegría!). Simplemente recuerde esta regla...

> [!NOTE]
> Si hay dos contenedores en la misma red, pueden comunicarse entre sí. Si no lo están, no se pueden.

## <a name="start-mysql"></a>Inicie MySQL

Hay dos maneras de colocar un contenedor en una red: asígnelo al inicio o Conecte un contenedor existente. Por ahora, creará la red primero y adjuntará el contenedor MySQL en el inicio.

1. Cree la red.

    ```bash
    docker network create todo-app
    ```

1. Inicie un contenedor MySQL y asócielo la red. También vamos a definir algunas variables de entorno que la base de datos usará para inicializar la base de datos (consulte la sección "variables de entorno" en la [lista de centros de Docker de MySQL](https://hub.docker.com/_/mysql/)) (Reemplace los ` \ ` caracteres por `` ` `` en Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    También verá que especificó la `--network-alias` marca. Volveremos a eso en un momento.

    > [!TIP]
    > Observará que está usando un nombre de volumen `todo-mysql-data` aquí y lo monta en `/var/lib/mysql` , que es donde MySQL almacena sus datos. Sin embargo, nunca se ejecutó un `docker volume create` comando. Docker reconoce que quiere usar un volumen con nombre y crea uno automáticamente.

1. Para confirmar que la base de datos está en funcionamiento, conéctese a la base de datos y compruebe que se conecta.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Cuando aparezca la solicitud de contraseña, escriba **Secret**. En el shell de MySQL, enumere las bases de datos y compruebe que ve la `todos` base de datos.

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

    Alegría! Tiene la `todos` base de datos y está lista para su uso.

## <a name="connect-to-mysql"></a>Conectarse a MySQL

Ahora que ya sabe que MySQL está en funcionamiento, vamos a utilizarlo. Pero la pregunta es... Qué? Si ejecuta otro contenedor en la misma red, ¿cómo se encuentra el contenedor (Recuerde que cada contenedor tiene su propia dirección IP)?

Para averiguarlo, va a usar el contenedor [nicolaka/netshoot](https://github.com/nicolaka/netshoot) , que se distribuye con *muchas* herramientas que son útiles para solucionar problemas o depurar problemas de red.

1. Inicie un nuevo contenedor mediante la `nicolaka/netshoot` imagen. Asegúrese de conectarse a la misma red.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Dentro del contenedor, use el `dig` comando, que es una herramienta DNS útil. Busque la dirección IP del nombre de host `mysql` .

    ```bash
    dig mysql
    ```

    Y obtendrá una salida similar a esta...

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

    En la sección "respuesta", verá un `A` registro de que se `mysql` resuelve en `172.23.0.2` (lo más probable es que la dirección IP tenga un valor diferente). Aunque `mysql` no es normalmente un nombre de host válido, Docker pudo resolverlo en la dirección IP del contenedor que tenía ese alias de red (recuerde la `--network-alias` marca que usó anteriormente?).

    Esto significa que es... la aplicación solo tiene que conectarse a un host con `mysql` el nombre y se comunicará con la base de datos. No es mucho más sencillo que eso.

## <a name="run-your-app-with-mysql"></a>Ejecutar la aplicación con MySQL

La aplicación todo admite la configuración de algunas variables de entorno para especificar la configuración de conexión de MySQL. Son las siguientes:

- `MYSQL_HOST` -el nombre de host para el servidor MySQL en ejecución
- `MYSQL_USER` -el nombre de usuario que se usará para la conexión
- `MYSQL_PASSWORD` -la contraseña que se usará para la conexión
- `MYSQL_DB` -la base de datos que se va a usar una vez conectada

> [!WARNING]
> **Establecer la configuración de conexión a través de variables de entorno** Aunque el uso de variables de entorno para establecer la configuración de conexión suele ser correcto para el desarrollo, no se recomienda cuando se ejecutan aplicaciones en producción. Para comprender por qué, consulte [por qué no debe usar variables de entorno para datos secretos](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Un mecanismo más seguro es usar la compatibilidad secreta que proporciona el marco de orquestación de contenedores. En la mayoría de los casos, estos secretos se montan como archivos en el contenedor en ejecución. Verá que muchas aplicaciones (incluida la imagen de MySQL y la aplicación de todo) también admiten los VARs de env con un `_FILE` sufijo para apuntar a un archivo que contiene el archivo.
> Por ejemplo, si se establece el valor `MYSQL_PASSWORD_FILE` var, la aplicación usará el contenido del archivo al que se hace referencia como la contraseña de conexión. Docker no hace nada para admitir estos VARs de env. La aplicación deberá saber que debe buscar la variable y obtener el contenido del archivo.

Con todo lo explicado, inicie el contenedor listo para desarrolladores.

1. Especifique cada una de las variables de entorno anteriores y conecte el contenedor a la red de la aplicación (Reemplace los ` \ ` caracteres por `` ` `` en Windows PowerShell).

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

1. Si examina los registros del contenedor ( `docker logs <container-id>` ), debería ver un mensaje que indica que se está usando la base de datos MySQL.

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

1. Conéctese a la base de datos MySQL y compruebe que los elementos se están escribiendo en la base de datos. Recuerde que la contraseña es **secreta**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    Y en el shell de MySQL, ejecute lo siguiente:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Obviamente, la tabla tendrá un aspecto diferente porque tiene los elementos. Pero debería ver que se almacenan allí.

Si echa un vistazo rápido a la extensión de Docker, verá que tiene dos contenedores de aplicaciones en ejecución. Sin embargo, no hay ninguna indicación real de que estén agrupadas en una sola aplicación. Verá cómo hacerlo mejor en breve.

![Extensión de Docker que muestra dos contenedores de aplicaciones sin agrupar](media/vs-multi-container-app.png)

## <a name="recap"></a>Resumen

En este momento, tiene una aplicación que almacena ahora sus datos en una base de datos externa que se ejecuta en un contenedor independiente. Ha aprendido un poco sobre las redes de contenedores y ha visto cómo se puede realizar la detección de servicios mediante DNS.

Pero hay una buena oportunidad de empezar a sentir un poco abrumado con todo lo que necesita hacer para iniciar esta aplicación. Tiene que crear una red, iniciar contenedores, especificar todas las variables de entorno, exponer puertos, etc. Eso es mucho para recordar y ciertamente dificulta el paso de las cosas a otra persona.

En la siguiente sección, hablaremos sobre Docker Compose. Con Docker Compose, puede compartir sus pilas de aplicaciones de una manera mucho más sencilla y permitir que otros las giren con un único comando (y simple).

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Usar Docker Compose](use-docker-compose.md)
