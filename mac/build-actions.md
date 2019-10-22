---
title: Acciones de compilación
description: En este artículo se describen las diversas acciones de compilación que se pueden realizar para los proyectos de C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 5a0d7c6646fac83ef70fbe2aa7384dcee992d726
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128445"
---
# <a name="build-actions"></a>Acciones de compilación

Todos los archivos de un proyecto de Visual Studio para Mac tienen una acción de compilación. La acción de compilación controla lo que sucede en el archivo durante una compilación. 

>[!NOTE]
>Este tema se aplica a Visual Studio para Mac. Para obtener información sobre Visual Studio en Windows, consulte [Acciones de compilación](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Establecer una acción de compilación

Para establecer una acción de compilación para un archivo en Visual Studio para Mac, puede hacer clic con el botón derecho en cualquier archivo y navegar a **Acción de compilación**, como se muestra a continuación:

![Selección de la acción de compilación en el Explorador de soluciones](media/projects-and-solutions-image1.png)

Las acciones de compilación para este archivo se mostrarán en el menú flotante. 

## <a name="build-action-values"></a>Valores de acción de compilación

A continuación se indican algunas de las acciones de compilación comunes para los proyectos que se pueden compilar en Visual Studio para Mac:

|Acción de compilación | Tipos de proyecto | DESCRIPCIÓN |
|--|--|--|
| **Compile** | any | El archivo se pasa al compilador de C# como un archivo de código fuente.|
| **Contenido** | .NET, Xamarin | En proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa. En proyectos de Xamarin.iOS y Xamarin.Mac, se incluyen en el lote de aplicaciones.|
| **Embedded Resource** | .NET | El archivo se pasa al compilador de C# como un recurso que se va a insertar en el ensamblado. [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream), del espacio de nombres `System.Reflection`, se puede usar para leer el archivo desde el ensamblado.|
| **Ninguno** | any | El archivo no forma parte de la compilación de ninguna manera; se incluye en el proyecto para facilitar el acceso desde el IDE. Este valor puede usarse para archivos de documentación como "Léame", por ejemplo.|

> [!NOTE]
> Tipos de proyecto específicos pueden definir otras acciones de compilación, por lo que la lista de acciones de compilación depende del tipo de proyecto y es posible que aparezcan valores que no están en esta lista.  

Los proyectos de Xamarin.iOS tienen la acción de compilación **BundleResource**, que agrega el archivo como parte del lote de aplicaciones. Puede encontrar información sobre acciones de compilación concretas de Xamarin.Android en la guía del [proceso de compilación](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

También es posible seleccionar más de un archivo en el Explorador de soluciones, lo que permite establecer la acción de compilación en muchos archivos a la vez.

## <a name="see-also"></a>Vea también

- [Build actions (Visual Studio on Windows)](/visualstudio/ide/build-actions) (Acciones de compilación [Visual Studio en Windows])