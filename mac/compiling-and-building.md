---
title: Compilar y generar en Visual Studio para Mac | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: abf772f1e00239b3a66e01c95dd827a392a12902
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Compilar y generar en Visual Studio para Mac

Visual Studio para Mac se puede usar para compilar aplicaciones y crear ensamblados durante el desarrollo del proyecto. Es importante compilar y crear el código desde el principio y con frecuencia para poder identificar errores de coincidencia de tipos y otros errores en tiempo de compilación.

## <a name="building-from-the-ide"></a>Compilar desde el IDE

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

## <a name="building-from-command-line"></a>Compilación desde la línea de comandos

Puede usar el motor de compilación MSBuild para compilar aplicaciones mediante la línea de comandos.

Vea el contenido de [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild) para más información sobre el uso de MSBuild.

## <a name="building-from-visual-studio-team-services"></a>Compilación desde Visual Studio Team Services

* [Build your Xamarin App (Compilar la aplicación Xamarin)](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Continuous Integration with Xamarin (Integración continua con Xamarin)](https://developer.xamarin.com/guides/cross-platform/ci/)