---
title: 'Tutorial de Docker, parte 4: conservar los datos'
description: Obtenga información acerca de cómo conservar los datos en una base de datos y compartir directorios en un contenedor mediante el montaje de un volumen.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 34b3cb9465c1efb946260917d755729e25c4e259
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176794"
---
# <a name="persist-your-data"></a> Conservación de los datos

En caso de que no haya observado, la lista de tareas pendientes se borra cada vez que se inicia el contenedor. ¿Por qué ocurre esto? Vamos a profundizar en cómo funciona el contenedor.

## <a name="the-containers-filesystem"></a>Sistema de archivos del contenedor

Cuando se ejecuta un contenedor, usa las distintas capas de una imagen para su sistema de archivos. Cada contenedor también obtiene su propio "espacio de desecho" para crear, actualizar o quitar archivos. Los cambios no se verán en otro contenedor, *incluso si* usan la misma imagen.

### <a name="see-this-in-practice"></a>Vea esto en la práctica

Para ver esto en acción, va a iniciar dos contenedores y creará un archivo en cada uno. Lo que verá es que los archivos creados en un contenedor no están disponibles en otro.

1. Inicie un `ubuntu` contenedor que creará un archivo denominado `/data.txt` con un número aleatorio entre 1 y 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    En caso de que tenga curiosidad sobre el comando, está iniciando un shell de Bash e invocando dos comandos (por qué tiene `&&` ). La primera parte elige un único número aleatorio y lo escribe en `/data.txt` . El segundo comando simplemente está inspeccionando un archivo para mantener el contenedor en ejecución.

1. Validar puede ver la salida mediante `exec` para obtener acceso al contenedor. Para ello, abra la extensión VS Code y, al hacer clic en la opción **asociar Shell** . Se usará `exec` para abrir un shell en el contenedor en el vs Code terminal.

    ![VS Code abrir la CLI en el contenedor Ubuntu](media/attach_shell.png)

    Verá un terminal que ejecuta un shell en el contenedor de Ubuntu. Ejecute el siguiente comando para ver el contenido del `/data.txt` archivo. Vuelva a cerrar este terminal después.

    ```bash
    cat /data.txt
    ```

    Si prefiere la línea de comandos, puede usar el `docker exec` comando para hacer lo mismo. Debe obtener el identificador del contenedor (use `docker ps` para obtenerlo) y obtener el contenido con el siguiente comando.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Debería ver un número aleatorio.

1. Ahora, inicie otro `ubuntu` contenedor (la misma imagen) y verá que no tiene el mismo archivo.

    ```bash
    docker run -it ubuntu ls /
    ```

    Y mire. No hay ningún `data.txt` archivo. Esto se debe a que se ha escrito en el espacio de desecho solo para el primer contenedor.

1. Continúe y quite el primer contenedor mediante el `docker rm -f` comando.

## <a name="container-volumes"></a>Volúmenes de contenedor

Con el experimento anterior, vio que cada contenedor se inicia a partir de la definición de imagen cada vez que se inicia. Aunque los contenedores pueden crear, actualizar y eliminar archivos, esos cambios se pierden cuando se quita el contenedor y todos los cambios se aíslan en ese contenedor. Con volúmenes, puede cambiar todo este.

Los [volúmenes](https://docs.docker.com/storage/volumes/) proporcionan la capacidad de conectar rutas de acceso de sistema de archivos específicas del contenedor al equipo host. Si se monta un directorio en el contenedor, los cambios en ese directorio también se verán en el equipo host. Si monta ese mismo directorio a través de reinicios de contenedor, vería los mismos archivos.

Hay dos tipos principales de volúmenes. en algún momento usará ambos, pero comenzará con **volúmenes con nombre**.

## <a name="persist-your-todo-data"></a>Conservar los datos de la lista de tareas

De forma predeterminada, la aplicación todo almacena sus datos en una base de datos [SQLite](https://www.sqlite.org/index.html) en `/etc/todos/todo.db` . Si no está familiarizado con SQLite, no le preocupa nada. Es simplemente una base de datos relacional en la que todos los datos se almacenan en un único archivo. Aunque esto no es lo mejor para las aplicaciones a gran escala, funciona para demostraciones pequeñas. Hablaremos sobre cómo cambiar esto a un motor de base de datos real más adelante.

Una vez que la base de datos es un único archivo, si puede conservar ese archivo en el host y hacer que esté disponible para el siguiente contenedor, debería poder recoger el lugar en el que quedó el último. Mediante la creación de un volumen y la Asociación (a menudo denominada "montaje") al directorio en el que se almacenan los datos, puede conservar los datos. A medida que el contenedor escribe en el `todo.db` archivo, se conserva en el host del volumen.

Como se mencionó, va a usar un **volumen con nombre**. Piense en un volumen con nombre como simplemente un depósito de datos. Docker mantiene la ubicación física en el disco y solo necesita recordar el nombre del volumen. Cada vez que se usa el volumen, Docker se asegurará de que se proporcionan los datos correctos.

1. Cree un volumen mediante el `docker volume create` comando.

    ```bash
    docker volume create todo-db
    ```

1. Detenga el contenedor de la aplicación todo una vez más en el panel (o con `docker rm -f <id>` ), ya que sigue ejecutándose sin usar el volumen persistente.

1. Inicie el contenedor de la aplicación todo, pero agregue la `-v` marca para especificar un montaje de volumen. usará el volumen con nombre y lo montará en `/etc/todos` , que capturará todos los archivos creados en la ruta de acceso.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Una vez que se inicia el contenedor, abra la aplicación y agregue algunos elementos a la lista de tareas pendientes.

    ![Elementos agregados a la lista de tareas pendientes](media/items-added.png)

1. Quite el contenedor de la aplicación todo. Use el panel o `docker ps` para obtener el identificador y, a continuación, `docker rm -f <id>` quitarlo.

1. Inicie un nuevo contenedor con el mismo comando anterior.

1. Abra la aplicación. Debería ver los elementos en la lista.

1. Continúe y quite el contenedor cuando haya terminado de desproteger la lista.

Alegría! Ahora ha aprendido a conservar los datos.

> [!TIP]
> Aunque los volúmenes con nombre y los montajes de enlace (que hablaremos en un minuto) son los dos tipos principales de volúmenes admitidos por la instalación de un motor de Docker predeterminado, hay muchos complementos de controlador de volumen disponibles para admitir NFS, SFTP, NetApp, etc. Esto será especialmente importante una vez que empiece a ejecutar contenedores en varios hosts en un entorno en clúster con Swarm, Kubernetes, etc.

## <a name="dive-into-your-volume"></a>Profundice en el volumen

Muchas personas suelen preguntar "¿Dónde se almacenan *realmente* mis datos cuando utilizo un volumen con nombre?". Si desea saber, puede usar el `docker volume inspect` comando.

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

`Mountpoint`Es la ubicación real en el disco donde se almacenan los datos. Tenga en cuenta que en la mayoría de los equipos, debe tener acceso a la raíz para acceder a este directorio desde el host. Pero es donde está.

> [!NOTE]
> **Acceso a los datos de volumen directamente en Docker Desktop** Mientras se ejecuta en Docker Desktop, los comandos de Docker se ejecutan realmente en una pequeña máquina virtual de la máquina. Si desea examinar el contenido real del directorio del *mountpoint* , deberá obtener primero en la máquina virtual. En WSL 2, se encuentra dentro de WSL 2 distribución y se puede acceder a él a través del explorador de archivos.

## <a name="recap"></a>Resumen

En este momento, tiene una aplicación que funciona y que puede sobrevivir a reinicios. Puede mostrarlo a sus inversores y esperar que puedan detectar su visión.

Sin embargo, antes vio que volver a generar imágenes para cada cambio tarda bastante tiempo. Hay una manera mejor de realizar cambios, ¿es correcto? Con montajes de enlace (que hemos sugerido en versiones anteriores), hay una manera mejor. Echemos un vistazo ahora.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Usar montajes de enlace](use-bind-mounts.md)
