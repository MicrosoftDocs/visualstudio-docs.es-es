---
title: Compilar y generar en Visual Studio para Mac
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: ea98f80d037a03912cf3d8212588ebb7520b4bbb
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---

# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilar y generar en Visual Studio para Mac

Visual Studio para Mac se puede usar para compilar aplicaciones y crear ensamblados durante el desarrollo del proyecto. Es importante compilar y crear el código desde el principio y con frecuencia para poder identificar errores de coincidencia de tipos y otros errores en tiempo de compilación.

## <a name="choosing-a-build-method"></a>Elección de un método de compilación:

### <a name="using-the-ide"></a>Uso de el IDE

Visual Studio para Mac permite crear y ejecutar compilaciones de forma inmediata y sin perder el control sobre la funcionalidad de compilación. Visual Studio para Mac usa MSBuild como sistema de compilación subyacente.

Todos los proyectos y soluciones creados en el IDE tienen una configuración de compilación predeterminada que define el contexto de las compilaciones. Se pueden editar estas configuraciones o crear unas propias. Al crear o modificar estas configuraciones se actualiza automáticamente el archivo de proyecto que luego usa MSBuild para compilar el proyecto.  

Para más información sobre cómo compilar proyectos y soluciones en el IDE, vea la guía [Compilar y limpiar proyectos y soluciones](~/building-and-cleaning-projects-and-solutions.md).

Visual Studio para Mac también se puede usar para lo siguiente:

* Cambiar la ruta de acceso de la salida. Se edita en las opciones del proyecto:

    ![Cambio de la ruta de acceso de la salida](media/compiling-and-building-image4.png)

* Cambiar el nivel de detalle de la salida de compilación:

    ![Cambio del nivel de detalle de la compilación](media/compiling-and-building-image5.png)

* Agregar comandos personalizados antes, durante o después de compilar o limpiar:

    ![adición de comandos personalizados](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>Compilación desde la línea de comandos

Puede usar el motor de compilación MSBuild para compilar aplicaciones mediante la línea de comandos.

Vea el contenido de [MSBuild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild) para más información sobre el uso de MSBuild.

### <a name="using-visual-studio-team-services"></a>Empleo de Visual Studio Team Services

* [Build your Xamarin App (Compilar la aplicación Xamarin)](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin)
* [Continuous Integration with Xamarin (Integración continua con Xamarin)](https://developer.xamarin.com/guides/cross-platform/ci/)
