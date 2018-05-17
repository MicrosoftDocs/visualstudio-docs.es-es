---
title: Acciones de compilación
description: En este artículo se describen las diversas acciones de compilación que se pueden realizar para los proyectos de C#
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 889414d391a4a894879399317d782df58a8bacb3
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="build-actions"></a>Acciones de compilación

Todos los archivos de un proyecto de Visual Studio para Mac tienen una acción de compilación que controla lo que le sucede al archivo durante una compilación. Puede configurarse si se hace clic con el botón derecho en cualquier archivo y se va a **Acción de compilación**, como se muestra debajo:

![Seleccionar la acción de compilación desde el Explorador de soluciones](media/projects-and-solutions-image1.png)

Algunas de las acciones de compilación comunes para proyectos de C# son:

* **None**: el archivo no es parte de la compilación de ninguna manera; solo se incluye en el proyecto para facilitar el acceso desde el IDE.
* **Compile**: el archivo se pasa al compilador de C# como un archivo de código fuente.
* **EmbeddedResource**: el archivo se pasa al compilador de C# como un recurso que se va a incrustar en el ensamblado. Luego se puede usar el espacio de nombres `System.Reflection` para leer el archivo desde el ensamblado.
* **Content**: en proyectos de ASP.NET, estos archivos se incluyen como parte del sitio cuando se implementa. En proyectos de Xamarin.iOS y Xamarin.Mac, se incluyen en el lote de aplicaciones.

Es posible seleccionar más de un archivo en el Explorador de soluciones, lo que permite establecer la acción de compilación de muchos archivos a la vez.

Además, hay acciones de compilación para proyectos específicos. Por ejemplo, los proyectos de Xamarin.iOS tienen la acción de compilación **BundleResource**, que agrega el archivo como parte del lote de aplicaciones. Puede encontrar información sobre acciones de compilación concretas de Xamarin.Android en la guía del [proceso de compilación](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions).