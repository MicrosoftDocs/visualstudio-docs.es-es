---
title: Administrar referencias en un proyecto
description: En este artículo se explica cómo administrar las referencias en un proyecto en Visual Studio para Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: a14630c5448632a939e1768040b910caf6276c2a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692915"
---
# <a name="managing-references-in-a-project"></a>Administrar referencias en un proyecto

Visual Studio para Mac ofrece dos maneras de agregar referencias adicionales a un proyecto:

![Referencias de proyectos](media/projects-and-solutions-image10.png)

Dichos componentes son:

* Referencias
* Paquetes NuGet (agregados a través de la carpeta Paquetes)

Además, también pueden agregarse referencias web y referencias nativas a un proyecto.

## <a name="assembly-references"></a>Referencias de ensamblado

Cada marco de trabajo dentro de Xamarin incluye más de una docena de ensamblados. Dentro del proyecto, no se hace referencia a todos estos paquetes de ensamblado de forma predeterminada.

Para editar los paquetes a los que se hace referencia en el proyecto, use el cuadro de diálogo **Editar referencias**, que se muestra al hacer doble clic en la carpeta Referencias o al seleccionar **Editar referencias** en las acciones de su menú contextual:

![Cuadro de diálogo Referencias de ensamblado](media/projects-and-solutions-image11.png)

Para obtener información sobre los ensamblados disponibles para cada marco de trabajo de Xamarin, vea la guía [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) (Ensamblados disponibles).

## <a name="nuget"></a>NuGet

NuGet es el administrador de paquetes más popular para el desarrollo de .NET. La compatibilidad con NuGet de Visual Studio para Mac permite buscar paquetes para agregarlos al proyecto.

Para ello, haga clic con el botón derecho en la carpeta **Paquete** en el Panel de la solución y seleccione Agregar paquetes.

En el tutorial [Including a NuGet package in your Project](nuget-walkthrough.md) (Incluir un paquete NuGet en el proyecto) se proporciona más información sobre el uso de un paquete NuGet.

## <a name="see-also"></a>Consulte también

- [Administrar referencias en un proyecto (Visual Studio en Windows)](/visualstudio/ide/managing-references-in-a-project)
- [Incorporación de referencias usando NuGet en lugar de un SDK de extensión (Visual Studio en Windows)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)