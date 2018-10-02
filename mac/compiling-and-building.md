---
title: Compilar y generar
description: En este artículo se explica cómo compilar y generar proyectos y soluciones en Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a66cc250b0d019b3efa4873b89eef252af44b8a6
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283709"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilar y generar en Visual Studio para Mac

Visual Studio para Mac se puede usar para compilar aplicaciones y crear ensamblados durante el desarrollo del proyecto. Es importante compilar y crear el código desde el principio y con frecuencia para poder identificar errores de coincidencia de tipos y otros errores en tiempo de compilación.

## <a name="building-from-the-ide"></a>Compilar desde el IDE

Visual Studio para Mac permite crear y ejecutar compilaciones de forma inmediata y sin perder el control sobre la funcionalidad de compilación. Visual Studio para Mac usa MSBuild como sistema de compilación subyacente.

Todos los proyectos y soluciones creados en el IDE tienen una configuración de compilación predeterminada que define el contexto de las compilaciones. Se pueden editar estas configuraciones o crear unas propias. Al crear o modificar estas configuraciones se actualiza automáticamente el archivo de proyecto que luego usa MSBuild para compilar el proyecto.

Para más información sobre cómo compilar proyectos y soluciones en el IDE, vea la guía [Compilar y limpiar proyectos y soluciones](building-and-cleaning-projects-and-solutions.md).

Visual Studio para Mac también se puede usar para lo siguiente:

* Cambiar la ruta de acceso de la salida. Se edita en las opciones del proyecto:

    ![Cambio de la ruta de acceso de la salida](media/compiling-and-building-image4.png)

* Cambiar el nivel de detalle de la salida de compilación:

    ![Cambio del nivel de detalle de la compilación](media/compiling-and-building-image5.png)

* Agregar comandos personalizados antes, durante o después de compilar o limpiar:

    ![adición de comandos personalizados](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Compilación desde la línea de comandos

Puede usar el motor de compilación MSBuild para compilar aplicaciones mediante la línea de comandos.

Vea el contenido de [MSBuild](/visualstudio/msbuild/msbuild) para más información sobre el uso de MSBuild.

## <a name="building-from-azure-pipelines"></a>Compilar desde Azure Pipelines

* [Build your Xamarin App (Compilar la aplicación Xamarin)](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Continuous Integration with Xamarin (Integración continua con Xamarin)](https://developer.xamarin.com/guides/cross-platform/ci/)