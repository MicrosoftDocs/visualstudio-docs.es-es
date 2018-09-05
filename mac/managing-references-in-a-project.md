---
title: Administrar referencias en un proyecto
description: En este artículo se explica cómo administrar las referencias en un proyecto en Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.openlocfilehash: 79d96ac61bcec198c899d709677df775332db383
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224016"
---
# <a name="managing-references-in-a-project"></a>Administrar referencias en un proyecto

Visual Studio para Mac ofrece dos maneras de agregar referencias adicionales a un proyecto:

![Referencias del proyecto](media/projects-and-solutions-image10.png)

Estos son:

* Referencias
* Paquetes NuGet (agregados a través de la carpeta Paquetes)

Además, también pueden agregarse referencias web y referencias nativas a un proyecto.

## <a name="assembly-references"></a>Referencias de ensamblado

Cada marco de trabajo dentro de Xamarin incluye más de una docena de ensamblados. Dentro del proyecto, no se hace referencia a todos estos paquetes de ensamblado de forma predeterminada. 

Para editar los paquetes a los que se hace referencia en el proyecto, use el cuadro de diálogo _Editar referencias_. Para mostrarlo, haga doble clic en la carpeta Referencias o seleccione Editar referencias en las acciones del menú contextual:

![Cuadro de diálogo Referencias de ensamblado](media/projects-and-solutions-image11.png)

Para obtener información sobre los ensamblados disponibles para cada marco de trabajo de Xamarin, vea la guía [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/) (Ensamblados disponibles).

## <a name="nuget"></a>NuGet

NuGet es el administrador de paquetes más popular para el desarrollo de .NET. La compatibilidad con NuGet de Visual Studio para Mac permite buscar paquetes para agregarlos al proyecto.

Para ello, haga clic con el botón derecho en la carpeta **Paquete** en el Panel de la solución y seleccione Agregar paquetes.

En el tutorial [Including a NuGet package in your Project](nuget-walkthrough.md) (Incluir un paquete NuGet en el proyecto) se proporciona más información sobre el uso de un paquete NuGet.
