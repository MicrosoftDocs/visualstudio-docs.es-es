---
title: 'Tutorial de Docker: Introducción a Docker'
description: Tutorial de varios pasos en el que se describen los conceptos básicos sobre cómo trabajar con Docker con Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176920"
---
# <a name="tutorial-get-started-with-docker"></a>Tutorial: Introducción a Docker

En este tutorial, aprenderá a crear e implementar aplicaciones de Docker, incluido el uso de varios contenedores con una base de datos y el uso de Docker Compose. También implementará la aplicación en contenedor en Azure.

## <a name="start-the-tutorial"></a>Inicio del tutorial

Si ya ha ejecutado el comando para empezar a trabajar con el tutorial, ¡ enhorabuena!  Si no es así, abra un símbolo del sistema o una ventana de bash y ejecute el comando:

```cli
docker run -d -p 80:80 docker/getting-started
```

Observará que se usan algunas marcas. Aquí encontrará información adicional:

- `-d` -ejecutar el contenedor en modo separado (en segundo plano)
- `-p 80:80` -asignar el puerto 80 del host al puerto 80 en el contenedor
- `docker/getting-started` -la imagen que se va a usar

> [!TIP]
> Puede combinar las marcas de un solo carácter para acortar el comando completo.
> Como ejemplo, el comando anterior podría escribirse de la siguiente manera:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>La extensión VS Code

Antes de pasar demasiado lejos, queremos resaltar la extensión de Docker VS Code, que le ofrece una vista rápida de los contenedores que se ejecutan en su equipo. Le proporciona acceso rápido a los registros de contenedor, le permite obtener un shell dentro del contenedor y le permite administrar fácilmente el ciclo de vida del contenedor (detener, quitar, etc.).

Para tener acceso a la extensión, siga las instrucciones que se indican [aquí](https://code.visualstudio.com/docs/containers/overview). Use el icono de Docker de la izquierda para abrir la vista de Docker. Si abre la extensión ahora, verá que se está ejecutando este tutorial. El nombre del contenedor ( `angry_taussig` a continuación) es un nombre creado aleatoriamente. Por lo tanto, lo más probable es que tenga un nombre diferente.

![Tutorial de ejecución de contenedor en la extensión Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Qué es un contenedor

Ahora que ha ejecutado un contenedor, ¿qué *es* un contenedor? En pocas palabras, un contenedor es simplemente otro proceso en el equipo que se ha aislado de todos los demás procesos del equipo host. Ese aislamiento aprovecha los [espacios de nombres del kernel y cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), las características que han estado en Linux durante mucho tiempo. Docker ha funcionado para que estas funcionalidades sean más fáciles de usar y fáciles de usar.

> [!NOTE]
> **Crear contenedores desde cero** Si desea ver cómo se crean los contenedores desde cero, Liz Rice de aguamarina Security tiene un vídeo en el que crea un contenedor desde cero en Go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Qué es una imagen de contenedor

Al ejecutar un contenedor, se usa un sistema de archivos aislado. Este sistema de archivos personalizado lo proporciona una **imagen de contenedor**. Como la imagen contiene el sistema de archivos del contenedor, debe contener todo lo necesario para ejecutar una aplicación: todas las dependencias, la configuración, los scripts, los archivos binarios, etc. La imagen también contiene otra configuración para el contenedor, como las variables de entorno, un comando predeterminado para ejecutar y otros metadatos.

Profundizaremos más en las imágenes más adelante, cubriendo temas como la disposición en capas, los procedimientos recomendados, etc.

> [!NOTE]
> Si está familiarizado con `chroot` , piense en un contenedor como una versión extendida de `chroot` . El sistema de archivos simplemente proviene de la imagen. Pero un contenedor agrega aislamiento adicional no disponible cuando se usa simplemente chroot.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [La aplicación](your-application.md)
