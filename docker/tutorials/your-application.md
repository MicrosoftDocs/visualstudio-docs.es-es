---
title: 'Tutorial de Docker - Parte 1: Compilación y ejecución de la aplicación de ejemplo de lista de tareas pendientes'
description: Introducción a la aplicación de ejemplo de lista de tareas pendientes que se ejecuta en Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 1b92792cf9db0090c52f583754e56c306e6d7234
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082583"
---
# <a name="build-and-run-the-todo-sample-app"></a>Compilación y ejecución de la aplicación de tareas pendientes de ejemplo

En el resto de este tutorial, trabajará con un sencillo administrador de lista de tareas pendientes que se ejecuta en Node.js. Si no está familiarizado con Node.js, no se preocupe. No se necesita ninguna experiencia real con JavaScript.

En este momento, el equipo de desarrollo es bastante pequeño y simplemente va a compilar una aplicación para demostrar el MVP (producto mínimo viable). Quiere mostrar cómo funciona y qué es capaz de hacer sin necesidad de pensar en su funcionamiento para un equipo grande, para varios desarrolladores, etc.

![Captura de pantalla del administrador de lista de tareas pendientes](media/todo-list-sample.png)

## <a name="get-the-app"></a>Obtener la aplicación

Antes de poder ejecutar la aplicación, debe disponer de su código fuente en el equipo. En el caso de proyectos reales, normalmente se clona el repositorio. Pero, para este tutorial, hemos creado un archivo ZIP que contiene la aplicación.

1. Asegúrese de que tiene instalado Docker para Windows o Docker Community Edition en el equipo local. Consulte la [documentación de instalación de Docker para Windows](https://docs.docker.com/docker-for-windows/install/). El proceso de instalación hace que el archivo ZIP que contiene el ejemplo esté disponible en la dirección localhost.

1. [Descargue el archivo ZIP](https://github.com/docker/getting-started/tree/master/app). Abra el archivo ZIP y asegúrese de extraer el contenido.

1. Una vez que lo haya extraído, use el editor de código que prefiera para abrir el proyecto. Si necesita un editor, puede usar [Visual Studio Code](https://code.visualstudio.com/). Debería ver `package.json` y dos subdirectorios (`src` y `spec`).

    ![Captura de pantalla de Visual Studio Code abierto con la aplicación cargada](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Compilación de la imagen de contenedor de la aplicación

Para compilar la aplicación, debe usar un objeto `Dockerfile`. Un Dockerfile es simplemente un script basado en texto de las instrucciones que se usa para crear una imagen de contenedor. Si ha creado Dockerfile antes, es posible que vea algunos errores en el que se muestra a continuación. Pero no se preocupe. Se explicarán individualmente.

1. Cree un archivo llamado `Dockerfile` en la misma carpeta del archivo `package.json` con el contenido siguiente.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Compruebe que el archivo `Dockerfile` no tiene ninguna extensión de archivo, como `.txt`. Algunos editores pueden anexar esta extensión de archivo de forma automática y esto daría lugar a un error en el paso siguiente.

1. Si todavía no lo ha hecho, abra un terminal y vaya al directorio `app` que contiene el objeto `Dockerfile`. Ahora, compile la imagen de contenedor mediante el comando `docker build`.

    ```bash
    docker build -t getting-started .
    ```

    Como alternativa, también puede hacer clic con el botón derecho en Dockerfile y elegir **Compilar imagen...** y, después, especificar la etiqueta en el símbolo del sistema.

    Este comando ha usado el Dockerfile para compilar una nueva imagen de contenedor. Es posible que haya observado que se han descargado muchas "capas". Se debe a que le ha indicado al generador que quiere comenzar a partir de la imagen `node:12-alpine`. Pero como no la tenía en el equipo, ha sido necesario descargarla.

    Una vez que se ha descargado la imagen, la ha copiado en la aplicación y ha usado `yarn` para instalar las dependencias de la aplicación. La directiva `CMD` especifica el comando predeterminado que se ejecutará al iniciar un contenedor a partir de esta imagen.

    Por último, la marca `-t` etiqueta la imagen. Puede considerarlo un nombre legible para la imagen final. Como ha asignado el nombre `getting-started` a la imagen, puede hacerle referencia al ejecutar un contenedor.

    El carácter `.` al final del comando `docker build` indica a Docker que debe buscar el objeto `Dockerfile` en el directorio actual.

## <a name="starting-an-app-container"></a>Inicio de un contenedor de aplicación

Ahora que tiene una imagen, ejecute la aplicación. Para ello, use el comando `docker run` (lo recordará de un apartado anterior).

1. Inicie el contenedor con el comando `docker run` y especifique el nombre de la imagen que acaba de crear:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    ¿Recuerda las marcas `-d` y `-p`? Va a ejecutar el nuevo contenedor en modo "desasociado" (en segundo plano) y a crear una asignación entre el puerto 3000 del host y el puerto 3000 del contenedor. Sin la asignación de puertos, no podría acceder a la aplicación.

1. Después de unos segundos, abra el explorador web en [http://localhost:3000](http://localhost:3000).
    Debería ver la aplicación.

    ![Lista de tareas pendientes vacía](media/todo-list-empty.png)

1. Continúe y agregue uno o dos elementos, y compruebe si funciona como esperaba. Puede marcar los elementos como completos y quitar elementos. El front-end almacena correctamente los elementos en el back-end. Bastante rápido y sencillo, ¿verdad?

Llegado a este punto, debería tener un administrador de lista de tareas pendientes operativo con algunos elementos, y todo lo ha compilado personalmente. Ahora, se realizarán algunos cambios y obtendrá información sobre cómo administrar los contenedores.

Si echa un vistazo rápido a la extensión VS Code, debería ver que ahora se ejecutan los dos contenedores (este tutorial y el contenedor de la aplicación recién iniciada).

![Extensión de Docker con los contenedores del tutorial y la aplicación en ejecución](media/vs-two-containers.png)

## <a name="recap"></a>Resumen

En esta breve sección, ha obtenido información sobre los conceptos básicos de la creación de una imagen de contenedor y ha creado un Dockerfile para ello. Después de crear la imagen, ha iniciado el contenedor y ha visto la aplicación en ejecución.

A continuación, realizará una modificación en la aplicación y aprenderá a actualizar la aplicación en ejecución con una imagen nueva. En el proceso, aprenderá algunos comandos útiles.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Actualización de la aplicación](update-your-app.md)
