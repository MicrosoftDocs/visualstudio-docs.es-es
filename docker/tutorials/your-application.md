---
title: 'Tutorial de Docker: parte 1: compilación y ejecución de la aplicación de ejemplo de lista de tareas'
description: Información general de la aplicación de ejemplo de lista de tareas que se ejecuta en Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: b8470c8d7708bc51916a6f57f5aa135c3267e355
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176917"
---
# <a name="build-and-run-the-todo-sample-app"></a>Compilar y ejecutar la aplicación de ejemplo todo

En el resto de este tutorial, trabajará con un administrador simple de la lista de tareas que se ejecuta en Node.js. Si no está familiarizado con Node.js, no se preocupe. No se necesita ninguna experiencia real de JavaScript.

En este momento, el equipo de desarrollo es bastante pequeño y simplemente está creando una aplicación para demostrar su MVP (producto mínimo viable). Desea mostrar cómo funciona y qué es capaz de hacer sin necesidad de pensar en cómo funcionará para un equipo grande, para varios desarrolladores, etc.

![Captura de pantalla del administrador de la lista de tareas](media/todo-list-sample.png)

## <a name="get-the-app"></a>Obtener la aplicación

Antes de poder ejecutar la aplicación, debe obtener el código fuente de la aplicación en la máquina. En el caso de los proyectos reales, normalmente se clonará el repositorio. Sin embargo, para este tutorial, ha creado un archivo ZIP que contiene la aplicación.

1. [Descargue el archivo zip](/assets/app.zip). Abra el archivo ZIP y asegúrese de extraer el contenido.

1. Una vez extraído, use el editor de código que prefiera para abrir el proyecto. Si necesita un editor, puede usar [Visual Studio Code](https://code.visualstudio.com/). Debería ver `package.json` y dos subdirectorios ( `src` y `spec` ).

    ![Captura de pantalla de Visual Studio Code abierto con la aplicación cargada](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Compilar la imagen de contenedor de la aplicación

Para compilar la aplicación, debe usar `Dockerfile` . Un Dockerfile es simplemente un script basado en texto de las instrucciones que se usa para crear una imagen de contenedor. Si ha creado Dockerfiles antes, es posible que vea algunos errores en el Dockerfile que aparece a continuación. Pero, no se preocupe. Nos pondremos en marcha.

1. Cree un archivo denominado `Dockerfile` en la misma carpeta que el archivo `package.json` con el siguiente contenido.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Compruebe que el archivo `Dockerfile` no tiene ninguna extensión de archivo como `.txt` . Algunos editores pueden anexar esta extensión de archivo automáticamente y esto daría lugar a un error en el paso siguiente.

1. Si todavía no lo ha hecho, abra un terminal y vaya al `app` directorio con el `Dockerfile` . Ahora compile la imagen de contenedor mediante el `docker build` comando.

    ```bash
    docker build -t getting-started .
    ```

    Este comando usaba Dockerfile para compilar una nueva imagen de contenedor. Es posible que haya observado que se han descargado muchas capas. Esto se debe a que ha indicado al generador que desea iniciar a partir de la `node:12-alpine` imagen. Sin embargo, puesto que no lo tenía en el equipo, la imagen necesitaba descargarse.

    Una vez descargada la imagen, se ha copiado en la aplicación y se ha usado `yarn` para instalar las dependencias de la aplicación. La `CMD` Directiva especifica el comando predeterminado que se ejecutará al iniciar un contenedor a partir de esta imagen.

    Por último, la `-t` marca etiqueta la imagen. Piense en esto simplemente como un nombre legible para la imagen final. Como ha llamado a la imagen `getting-started` , puede hacer referencia a esa imagen al ejecutar un contenedor.

    Al `.` final del `docker build` comando, indica que Docker debe buscar `Dockerfile` en el directorio actual.

## <a name="starting-an-app-container"></a>Inicio de un contenedor de la aplicación

Ahora que tiene una imagen, ejecute la aplicación. Para ello, use el `docker run` comando (Recuerde que, con anterioridad?).

1. Inicie el contenedor con el `docker run` comando y especifique el nombre de la imagen que acaba de crear:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    ¿Recuerda `-d` las `-p` marcas y? Está ejecutando el nuevo contenedor en modo "desasociado" (en segundo plano) y creando una asignación entre el puerto del host 3000 y el puerto 3000 del contenedor. Sin la asignación de puertos, no podrá tener acceso a la aplicación.

1. Después de unos segundos, abra el explorador Web en [http://localhost:3000](http://localhost:3000) .
    Debería ver la aplicación.

    ![Lista de tareas vacía](media/todo-list-empty.png)

1. Continúe y agregue un elemento o dos y vea que funciona como se espera. Puede marcar elementos como completos y quitar elementos. El front-end está almacenando correctamente los elementos en el back-end. ¿Es bastante rápido y sencillo, EH?

En este punto, debe tener un administrador de la lista de tareas pendientes con algunos elementos, todo ello compilado. Ahora, vamos a realizar algunos cambios y obtener información sobre cómo administrar los contenedores.

Si echa un vistazo rápido a la extensión de VS Code, debería ver que los dos contenedores se ejecutan ahora (este tutorial y el contenedor de la aplicación recién iniciado).

![Extensión de Docker con el tutorial y contenedores de aplicaciones en ejecución](media/vs-two-containers.png)

## <a name="recap"></a>Resumen

En esta breve sección, ha aprendido los conceptos básicos sobre la creación de una imagen de contenedor y la creación de un Dockerfile para ello. Una vez creada la imagen, ha iniciado el contenedor y ha visto la aplicación en ejecución.

A continuación, va a realizar una modificación en la aplicación y aprenderá a actualizar la aplicación en ejecución con una nueva imagen. A lo largo del proceso, aprenderá algunos comandos útiles.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Actualización de la aplicación](update-your-app.md)