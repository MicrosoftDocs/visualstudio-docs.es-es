---
title: Acciones de compilación
description: En este artículo se describen las diversas acciones de compilación que se pueden realizar para los proyectos de C#
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 16617f8de15fbef40941c4f9409497da142c9e8a
ms.sourcegitcommit: f61ad0e8babec8810295f039e67629f4bdebeef0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "52001183"
---
# <a name="build-actions"></a>Acciones de compilación

Todos los archivos de un proyecto de Visual Studio para Mac tienen una acción de compilación. Controla lo que sucede en el archivo durante una compilación. Este comportamiento puede configurarse si se hace clic con el botón derecho en cualquier archivo y se va a **Acción de compilación**, como se muestra debajo:

![Selección de la acción de compilación en el Explorador de soluciones](media/projects-and-solutions-image1.png)

Algunas de las acciones de compilación comunes para proyectos de C# son:

* **None**: el archivo no forma parte de la compilación de ninguna manera; se incluye en el proyecto para facilitar el acceso desde el IDE.
* **Compile**: el archivo se pasa al compilador de C# como un archivo de código fuente.
* **EmbeddedResource**: el archivo se pasa al compilador de C# como un recurso que se va a incrustar en el ensamblado. [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream), del espacio de nombres `System.Reflection`, se puede usar para leer el archivo desde el ensamblado.
* **Content**: en proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa. En proyectos de Xamarin.iOS y Xamarin.Mac, se incluyen en el lote de aplicaciones.

Es posible seleccionar más de un archivo en el Explorador de soluciones, lo que permite establecer la acción de compilación en muchos archivos a la vez.

Además, hay acciones de compilación para proyectos específicos. Los proyectos de Xamarin.iOS tienen la acción de compilación **BundleResource**, que agrega el archivo como parte del lote de aplicaciones. Puede encontrar información sobre acciones de compilación concretas de Xamarin.Android en la guía del [proceso de compilación](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).

## <a name="see-also"></a>Vea también

- [Build actions (Visual Studio on Windows)](/visualstudio/ide/build-actions) (Acciones de compilación [Visual Studio en Windows])