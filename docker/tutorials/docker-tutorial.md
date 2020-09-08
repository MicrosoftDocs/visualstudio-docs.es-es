---
title: 'Tutorial de Docker: Introducción a Docker'
description: Tutorial de varios pasos en el que se describen los conceptos básicos sobre cómo trabajar con Docker con Visual Studio Code.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176920"
---
# <a name="tutorial-get-started-with-docker"></a>Tutorial: Introducción a Docker

En este tutorial, aprenderá a crear e implementar aplicaciones de Docker, incluido el uso de varios contenedores con una base de datos y el uso de Docker Compose. También implementará en Azure la aplicación en contenedores.

## <a name="start-the-tutorial"></a>Inicio del tutorial

Si ya ha ejecutado el comando para empezar a trabajar con el tutorial, enhorabuena.  En caso contrario, abra una ventana de símbolo del sistema o Bash, y ejecute el comando siguiente:

```cli
docker run -d -p 80:80 docker/getting-started
```

Observará que se usan algunas marcas. La siguiente es información adicional sobre ellas:

- `-d`: el contenedor se ejecuta en modo desasociado (en segundo plano)
- `-p 80:80`: el puerto 80 del host se asigna al puerto 80 del contenedor
- `docker/getting-started`: imagen que se va a usar

> [!TIP]
> Puede combinar las marcas de un solo carácter para acortar el comando completo.
> Como ejemplo, el comando anterior se podría escribir de esta forma:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>La extensión VS Code

Antes de continuar demasiado lejos, conviene destacar la extensión VS Code de Docker, en la que se ofrece una vista rápida de los contenedores que se ejecutan en el equipo. Proporciona acceso rápido a los registros de contenedor, permite obtener un shell dentro del contenedor y administrar con facilidad el ciclo de vida del contenedor (detenerlo, quitarlo, etc.).

Para acceder a la extensión, siga [estas](https://code.visualstudio.com/docs/containers/overview) instrucciones. Use el icono de Docker de la izquierda para abrir la vista de Docker. Si abre ahora la extensión, verá que se ejecuta este tutorial. El nombre del contenedor (`angry_taussig` a continuación) se ha creado aleatoriamente. Por tanto, lo más probable es que tenga otro nombre.

![Contenedor del tutorial en ejecución en la extensión Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Concepto de contenedor

Ahora que ha ejecutado un contenedor, ¿qué *es* un contenedor? En pocas palabras, un contenedor es simplemente otro proceso en el equipo que se ha aislado de todos los demás procesos del equipo host. Ese aislamiento aprovecha [espacios de nombres del kernel y cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), características presentes en Linux desde hace mucho tiempo. Docker ha trabajado para que estas funcionalidades sean más fáciles de usar.

> [!NOTE]
> **Creación de contenedores desde cero** Si quiere ver cómo se crean los contenedores desde cero, Liz Rice de Aqua Security tiene un vídeo en el que crea un contenedor desde cero en Go:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Definición de imagen de contenedor

Al ejecutar un contenedor, usa un sistema de archivos aislado. Este sistema de archivos personalizado se proporciona mediante una **imagen de contenedor**. Como la imagen contiene el sistema de archivos del contenedor, debe incluir todo lo necesario para ejecutar una aplicación: todas las dependencias, la configuración, los scripts, los archivos binarios, etc. La imagen también contiene otra configuración para el contenedor, como las variables de entorno, un comando predeterminado para ejecutar y otros metadatos.

Más adelante se profundizará en las imágenes y se describirán temas como la disposición en capas, los procedimientos recomendados, etc.

> [!NOTE]
> Si está familiarizado con `chroot`, piense en un contenedor como una versión extendida de `chroot`. El sistema de archivos simplemente proviene de la imagen. Pero un contenedor agrega aislamiento adicional que no está disponible cuando solo se usa chroot.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [La aplicación](your-application.md)
