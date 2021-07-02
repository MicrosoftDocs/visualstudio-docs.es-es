---
title: 'Tutorial de Docker - Parte 5: Uso de montajes de enlace'
description: Se describe cómo usar montajes de enlace para controlar el punto de montaje en el host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad3737ccfa4b0dae8ad427bd79e4adeb2756795b
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222765"
---
# <a name="use-bind-mounts"></a>Uso de montajes de enlace

En el capítulo anterior, ha obtenido información sobre los **volúmenes con nombre** y ha usado uno para conservar los datos en la base de datos. Los volúmenes con nombre son excelentes si simplemente quiere almacenar los datos, sin preocuparse de *dónde* se almacenan.

Con los **montajes de enlace**, puede controlar el punto de montaje exacto en el host. Puede usarlo para conservar los datos, pero se suele utilizar para proporcionar datos adicionales a contenedores. Cuando se trabaja en una aplicación, se puede usar un montaje de enlace para montar el código fuente en el contenedor y ver los cambios de código, responder y poder ver los cambios inmediatamente.

En el caso de las aplicaciones basadas en Node, [nodemon](https://npmjs.com/package/nodemon) es una herramienta excelente para inspeccionar los cambios en los archivos y, después, reiniciar la aplicación. Existen herramientas equivalentes en la mayoría de los lenguajes y marcos.

## <a name="quick-volume-type-comparisons"></a>Comparaciones de tipo de volumen rápidas

Los montajes de enlace y los volúmenes con nombre son los dos tipos principales de volúmenes que se incluyen con el motor de Docker. Pero hay controladores de volumen adicionales disponibles para admitir otros casos de uso ([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume) y muchos más).

| Propiedad | Volúmenes con nombre | Enlazar montajes |
| -------- | ------------- | ----------- |
| Ubicación del host | Elección de Docker | El control |
| Ejemplo de montaje (con `-v`) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Rellena el nuevo volumen con el contenido del contenedor | Sí | No |
| Admite controladores de volumen | Sí | No |

## <a name="start-a-dev-mode-container"></a>Inicio de un contenedor en modo de desarrollo

Para ejecutar el contenedor a fin de admitir un flujo de trabajo de desarrollo, siga estos pasos:

- Monte el código fuente en el contenedor
- Instale todas las dependencias, incluidas las de "desarrollo"
- Inicie nodemon para ver los cambios en el sistema de archivos

1. Asegúrese de que no tiene ningún contenedor `getting-started` anterior en ejecución.

1. Ejecute el comando siguiente (reemplace los caracteres ` \ ` por `` ` `` en Windows PowerShell). Más adelante verá lo que ocurre:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000`: igual que antes. Se ejecuta en modo desasociado (en segundo plano) y se crea una asignación de puerto
    - `-w /app`: establece el "directorio de trabajo" o el directorio actual desde el que se ejecutará el comando.
    - `-v "%cd%:/app"`: montaje de enlace del directorio actual desde el host del contenedor en el directorio `/app`
    - `node:12-alpine`: la imagen que se va a usar. Se trata de la imagen base para la aplicación del Dockerfile
    - `sh -c "yarn install && yarn run dev"`: el comando. Se inicia un shell mediante `sh` (alpine carece de `bash`), se ejecuta `yarn install` para instalar *todas* las dependencias y, después, se ejecuta `yarn run dev`. Si observa `package.json`, verá que el script `dev` inicia `nodemon`.

1. Puede ver los registros mediante `docker logs -f <container-id>`. Sabrá que está listo para empezar cuando vea lo siguiente:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Cuando haya terminado de ver los registros, presione `Ctrl`+`C` para salir.

1. Ahora, realice un cambio en la aplicación. En el archivo `src/static/js/app.js`, cambie el botón **Agregar elemento** por simplemente **Agregar**. Este cambio estará en la línea 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Solo tiene que actualizar la página (o abrirla) y debería ver el cambio reflejado en el explorador casi de forma inmediata. Es posible que el servidor de Node tarde unos segundos en reiniciarse, por lo que si se produce un error, simplemente intente actualizar después de unos segundos.

    ![Captura de pantalla de la etiqueta actualizada para el botón Agregar](media/updated-add-button.png)

1. No dude en realizar cualquier otro cambio que quiera. Cuando haya terminado, detenga el contenedor y compila la imagen mediante `docker build -t getting-started .`.

El uso de montajes de enlace es *muy* común para las configuraciones de desarrollo local. La ventaja es que el equipo de desarrollo no necesita tener todas las herramientas de compilación y los entornos instalados. Con un solo comando `docker run`, se extrae el entorno de desarrollo y está listo para empezar. En un paso posterior, obtendrá información sobre Docker Compose, que le ayudará a simplificar los comandos (ya acumula muchas marcas).

## <a name="recap"></a>Resumen

Llegado a este punto, puede conservar la base de datos y responder rápidamente a las necesidades y demandas de inversores y fundadores. Enhorabuena. ¿Pero sabe qué? Ha recibido excelentes noticias.

**Han seleccionado el proyecto para continuar el desarrollo.**

A fin de prepararse para la producción, debe migrar la base de datos de SQLite a algo que se pueda escalar un poco mejor. Para simplificar, mantendrá una base de datos relacional y cambiará la aplicación para que use MySQL. ¿Pero cómo debe ejecutar MySQL? ¿Cómo permite que los contenedores se comuniquen entre sí? Lo verá a continuación.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Aplicaciones de varios contenedores](multi-container-apps.md)