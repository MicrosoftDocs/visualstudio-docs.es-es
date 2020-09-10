---
title: 'Tutorial de Docker - Parte 4: Conservación de los datos'
description: Obtenga información sobre cómo conservar los datos en una base de datos y compartir directorios en un contenedor mediante el montaje de un volumen.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9a4eb5062f8f1b01e8ad5e5165d7ec9ede636124
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485591"
---
# <a name="persist-your-data"></a> Conservación de los datos

En caso de que no lo haya observado, la lista de tareas pendientes se borra cada vez que se inicia el contenedor. ¿Por qué ocurre esto? Ahora se profundizará en cómo funciona el contenedor.

## <a name="the-containers-filesystem"></a>Sistema de archivos del contenedor

Cuando se ejecuta un contenedor, usa las distintas capas de una imagen para su sistema de archivos. Cada contenedor también obtiene su propio "espacio de desecho" para crear, actualizar o quitar archivos. Los cambios no se verán en otro contenedor, *incluso aunque* usen la misma imagen.

### <a name="see-this-in-practice"></a>Demostración práctica

Para verlo en acción, iniciará dos contenedores y creará un archivo en cada uno. Lo que verá es que los archivos creados en un contenedor no están disponibles en el otro.

1. Inicie un contenedor `ubuntu` que creará un archivo denominado `/data.txt` con un número aleatorio entre 1 y 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Si tiene curiosidad sobre el comando, lo que hace es iniciar un shell de Bash e invocar dos comandos (de ahí la presencia de `&&`). En la primera parte se elige un único número aleatorio y se escribe en `/data.txt`. El segundo comando simplemente inspecciona un archivo para mantener el contenedor en ejecución.

1. Compruebe si puede ver la salida mediante `exec` para acceder al contenedor. Para ello, abra la extensión VS Code y al haga clic en la opción **Attach Shell** (Adjuntar shell). Se usará `exec` para abrir un shell en el contenedor dentro del terminal de VS Code.

    ![Apertura de la CLI de VS Code en el contenedor de Ubuntu](media/attach_shell.png)

    Verá un terminal que ejecuta un shell en el contenedor de Ubuntu. Ejecute el comando siguiente para ver el contenido del archivo `/data.txt`. Vuelva a cerrar este terminal después.

    ```bash
    cat /data.txt
    ```

    Si prefiere la línea de comandos, puede usar el comando `docker exec` para hacer lo mismo. Tendrá que obtener el identificador del contenedor (use `docker ps` para obtenerlo) y el contenido con el comando siguiente.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Debería ver un número aleatorio.

1. Ahora, inicie otro contenedor `ubuntu` (la misma imagen) y verá que no tiene el mismo archivo.

    ```bash
    docker run -it ubuntu ls /
    ```

    Fíjese. No hay ningún archivo `data.txt`. Se debe a que se ha escrito en el espacio de desecho solo para el primer contenedor.

1. Continúe y quite el primer contenedor mediante el comando `docker rm -f`.

## <a name="container-volumes"></a>Volúmenes de contenedor

Con el experimento anterior, ha visto que cada contenedor se inicia a partir de la definición de imagen cada vez que se inicia. Aunque los contenedores pueden crear, actualizar y eliminar archivos, esos cambios se pierden cuando se quita el contenedor y todos los cambios se aíslan en él. Con lo volúmenes, puede cambiar todo este comportamiento.

Los [volúmenes](https://docs.docker.com/storage/volumes/) proporcionan la capacidad de conectar rutas de acceso específicas del sistema de archivos del contenedor con el equipo host. Si se monta un directorio en el contenedor, los cambios en ese directorio también se verán en el equipo host. Si monta ese mismo directorio entre reinicios de contenedor, vería los mismos archivos.

Hay dos tipos principales de volúmenes. En última instancia usará los dos, pero comenzará con los **volúmenes con nombre**.

## <a name="persist-your-todo-data"></a>Conservación de los datos de tareas pendientes

De forma predeterminada, la aplicación de tareas pendientes almacena sus datos en una [base de datos de SQLite](https://www.sqlite.org/index.html) en `/etc/todos/todo.db`. Si no está familiarizado con SQLite, no se preocupe. Es simplemente una base de datos relacional en la que todos los datos se almacenan en un único archivo. Aunque esto no sea lo mejor para las aplicaciones a gran escala, funciona para demostraciones pequeñas. Más adelante se explicará cómo cambiarlo por un motor de base de datos real.

Como la base de datos es un único archivo, si puede conservar ese archivo en el host y hacer que esté disponible para el siguiente contenedor, debería poder retomar desde el punto en que lo haya dejado el último. Si crea un volumen y lo adjunta (lo que se suele denominar "montaje") al directorio en el que se almacenan los datos, puede conservar los datos. A medida que el contenedor escribe en el archivo `todo.db`, se conserva en el host del volumen.

Como se ha mencionado antes, usará un **volumen con nombre**. Piense en un volumen con nombre como en un simple depósito de datos. Docker mantiene la ubicación física en el disco y solo tendrá que recordar el nombre del volumen. Cada vez que use el volumen, Docker se asegurará de que se proporcionan los datos correctos.

1. Cree un volumen mediante el comando `docker volume create`.

    ```bash
    docker volume create todo-db
    ```

1. Detenga el contenedor de la aplicación de tareas pendientes una vez más en la vista de Docker (o con `docker rm -f <id>`), ya que se sigue ejecutando sin usar el volumen persistente.

1. Inicie el contenedor de la aplicación de tareas pendientes, pero agregue la marca `-v` para especificar un montaje de volumen. Usará el volumen con nombre y lo montará en `/etc/todos`, que capturará todos los archivos creados en la ruta de acceso.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Una vez que se inicie el contenedor, abra la aplicación y agregue varios elementos a la lista de tareas pendientes.

    ![Elementos agregados a la lista de tareas pendientes](media/items-added.png)

1. Quite el contenedor de la aplicación de tareas pendientes. Use la vista de Docker o `docker ps` para obtener el identificador, y después `docker rm -f <id>` para quitarlo.

1. Inicie un contenedor nuevo con el mismo comando anterior.

1. Abra la aplicación. Debería ver los elementos en la lista.

1. Continúe y quite el contenedor cuando haya terminado de comprobar la lista.

Enhorabuena. Ha aprendido a conservar los datos.

> [!TIP]
> Aunque los volúmenes con nombre y los montajes de enlace (que se describirán en breve) son los dos tipos principales de volúmenes admitidos por la instalación de un motor de Docker predeterminado, hay muchos complementos de controlador de volumen disponibles para admitir NFS, SFTP, NetApp, etc. Esto será especialmente importante una vez que empiece a ejecutar contenedores en varios hosts en un entorno en clúster con Swarm, Kubernetes, etc.

## <a name="dive-into-your-volume"></a>Profundización en el volumen

Muchas usuarios se suelen preguntar: "¿Dónde almacena Docker *realmente* los datos cuando se usa un volumen con nombre?" Si quiere saberlo, puede usar el comando `docker volume inspect`.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint` es la ubicación real en el disco donde se almacenan los datos. Tenga en cuenta que en la mayoría de los equipos, necesitará tener acceso a raíz para acceder a este directorio desde el host. Pero ahí es donde se encuentran.

> [!NOTE]
> **Acceso a los datos del volumen directamente en Docker Desktop** Mientras ejecuta Docker Desktop, los comandos de Docker se ejecutan realmente en una pequeña máquina virtual del equipo. Si quiere examinar el contenido real del directorio *Mountpoint*, primero tendrá que acceder a la máquina virtual. En WSL 2, esto es el interior de un distribución WSL 2 y se puede acceder a través del Explorador de archivos.

## <a name="recap"></a>Resumen

En este momento, tiene una aplicación que funciona y que puede sobrevivir a los reinicios. Puede mostrársela a los inversores con la esperanza de que capten la idea.

Pero antes ha comprobado que volver a generar las imágenes para cada cambio lleva bastante tiempo. Tiene que haber una manera mejor de realizar cambios, ¿no es cierto? Con los montajes de enlace (que se han mencionado antes), hay una manera mejor de hacerlo. Es lo que verá ahora.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Uso de montajes de enlace](use-bind-mounts.md)
