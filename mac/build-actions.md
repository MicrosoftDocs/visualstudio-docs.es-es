---
title: "Acciones de compilación"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 78b0e715ca44c613b6a7ee839c0656e301308588
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2017
---
# <a name="build-actions"></a>Acciones de compilación 

Todos los archivos de un proyecto de Visual Studio para Mac tienen una acción de compilación que controla lo que le sucede al archivo durante una compilación. Puede configurarse si se hace clic con el botón derecho en cualquier archivo y se va a **Acción de compilación**, como se muestra debajo:

![](media/projects-and-solutions-image1.png)

Algunas de las acciones de compilación comunes para proyectos de C# son:

* **None**: el archivo no es parte de la compilación de ninguna manera; solo se incluye en el proyecto para facilitar el acceso desde el IDE.
* **Compile**: el archivo se pasa al compilador de C# como un archivo de código fuente.
* **EmbeddedResource**: el archivo se pasa al compilador de C# como un recurso que se va a incrustar en el ensamblado. Luego se puede usar el espacio de nombres `System.Reflection` para leer el archivo desde el ensamblado.
* **Content**: en proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa. En proyectos de Xamarin.iOS y Xamarin.Mac, se incluyen en el lote de aplicaciones.

Es posible seleccionar más de un archivo en el Explorador de soluciones, lo que permite establecer la acción de compilación de muchos archivos a la vez.

Además, hay acciones de compilación para proyectos específicos. Por ejemplo, los proyectos de Xamarin.iOS tienen la acción de compilación **BundleResource**, que agrega el archivo como parte del lote de aplicaciones. Puede encontrar información sobre acciones de compilación concretas de Xamarin.Android en la guía del [proceso de compilación](https://developer.xamarin.com/guides/android/under_the_hood/build_process/#Build_Actions) en developer.xamarin.com.