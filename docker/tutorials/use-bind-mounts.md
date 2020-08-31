---
title: 'Tutorial de Docker: parte 5: uso de montajes de enlace'
description: Describe cómo usar montajes de enlace para controlar el punto de montaje en el host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176916"
---
# <a name="use-bind-mounts"></a>Usar montajes de enlace

En el capítulo anterior, aprendió y usó un **volumen con nombre** para conservar los datos en la base de datos. Los volúmenes con nombre son excelentes si simplemente desea almacenar los datos, ya que no tiene que preocuparse de *dónde* se almacenan los datos.

Con los **montajes de enlace**, puede controlar el mountpoint exacto en el host. Puede utilizar esto para conservar los datos, pero se suele usar para proporcionar datos adicionales en los contenedores. Cuando se trabaja en una aplicación, se puede usar un montaje de enlace para montar el código fuente en el contenedor para que pueda ver los cambios de código, responder y permitirle ver los cambios inmediatamente.

En el caso de las aplicaciones basadas en nodos, [nodemon](https://npmjs.com/package/nodemon) es una excelente herramienta para inspeccionar los cambios en los archivos y, a continuación, reiniciar la aplicación. Existen herramientas equivalentes en la mayoría de los lenguajes y marcos de trabajo.

## <a name="quick-volume-type-comparisons"></a>Comparaciones de tipo de volumen rápido

Los montajes de enlace y los volúmenes con nombre son los dos tipos principales de volúmenes que se incluyen con el motor de Docker. Sin embargo, hay controladores de volumen adicionales disponibles para admitir otros casos de uso ([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume), etc.).

| Propiedad | Volúmenes con nombre | Enlazar montajes |
| -------- | ------------- | ----------- |
| Ubicación del host | Elección de Docker | Usted controla |
| Ejemplo de montaje (con `-v` ) | My-Volume:/usr/local/Data | /path/to/data:/usr/local/data |
| Rellena el nuevo volumen con el contenido del contenedor | Sí | No |
| Admite controladores de volumen | Sí | No |

## <a name="start-a-dev-mode-container"></a>Inicio de un contenedor en modo de desarrollo

Para ejecutar el contenedor para admitir un flujo de trabajo de desarrollo, haga lo siguiente:

- Montaje del código fuente en el contenedor
- Instalación de todas las dependencias, incluidas las dependencias de "dev"
- Iniciar nodemon para ver los cambios del sistema de archivos

1. Asegúrese de que no tiene ningún contenedor anterior en `getting-started` ejecución.

1. Ejecute el siguiente comando (Reemplace los ` \ ` caracteres por `` ` `` en Windows PowerShell). Aprenderá lo que ocurre después:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` : igual que antes. Ejecutar en modo desasociado (en segundo plano) y crear una asignación de Puerto
    - `-w /app` : establece el "directorio de trabajo" o el directorio actual desde el que se ejecutará el comando.
    - `-v ${PWD}:/app` -BIND monta el directorio actual desde el host del contenedor en el `/app` directorio.
    - `node:12-alpine` : la imagen que se va a usar. Tenga en cuenta que se trata de la imagen base de la aplicación desde el Dockerfile
    - `sh -c "yarn install && yarn run dev"` : el comando. Vamos a iniciar un shell con `sh` (Alpine no tiene `bash` ) y `yarn install` en ejecución para instalar *todas las* dependencias y, a continuación, ejecutar `yarn run dev` . Si observa, veremos `package.json` que el `dev` script se está iniciando `nodemon` .

1. Puede ver los registros mediante `docker logs -f <container-id>` . Sabrá que está listo para empezar cuando vea lo siguiente:

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

    Cuando haya terminado de ver los registros, salga `Ctrl` + `C` .

1. Ahora, realice un cambio en la aplicación. En el `src/static/js/app.js` archivo, cambie el botón **Agregar elemento** por simplemente **Agregar**. Este cambio estará en la línea 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Simplemente actualice la página (o ábrala) y debería ver el cambio reflejado en el explorador casi inmediatamente. Es posible que el servidor de nodos tarde unos segundos en reiniciarse, por lo que si se produce un error, simplemente intente actualizar después de unos segundos.

    ![Captura de pantalla de la etiqueta actualizada para el botón Agregar](media/updated-add-button.png)

1. No dude en realizar cualquier otro cambio que desee realizar. Cuando haya terminado, detenga el contenedor y cree la imagen nueva con `docker build -t getting-started .` .

El uso de montajes de enlace es *muy* común para las configuraciones de desarrollo local. La ventaja es que el equipo de desarrollo no necesita tener todas las herramientas de compilación y los entornos instalados. Con un solo `docker run` comando, se extrae el entorno de desarrollo y está listo para empezar. En un paso posterior, obtendrá información sobre Docker Compose, ya que esto le ayudará a simplificar los comandos (ya está obteniendo muchas marcas).

## <a name="recap"></a>Resumen

Llegados a este punto, puede conservar la base de datos y responder rápidamente a las necesidades y demandas de los inversores y fundadores. Alegría! Pero, ¿adivina qué? Ha recibido excelentes noticias.

**El proyecto se ha seleccionado para desarrollo futuro.**

Para prepararse para la producción, debe migrar la base de datos del trabajo en SQLite a algo que pueda escalar un poco mejor. Para simplificar, mantendrá con una base de datos relacional y cambiará la aplicación para usar MySQL. Pero, ¿cómo se debe ejecutar MySQL? ¿Cómo permite que los contenedores se comuniquen entre sí? Aprenderá lo siguiente.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Aplicaciones de varios contenedores](multi-container-apps.md)