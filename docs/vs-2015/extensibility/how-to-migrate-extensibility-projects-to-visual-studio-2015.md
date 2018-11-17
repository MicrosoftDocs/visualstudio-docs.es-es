---
title: 'Cómo: migrar proyectos de extensibilidad a Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564e279d259cae879ca2925eed3309c30d7513db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785162"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Cómo: migrar proyectos de extensibilidad a Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aquí le mostramos cómo actualizar la extensión.  
  
> [!IMPORTANT]
>  Si piensa mantener una versión de la solución de extensión para una versión anterior de Visual Studio, asegúrese de realizar una copia antes de que la actualización. Puede ser difícil devolver la versión actualizada a su estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para actualizar una solución de extensibilidad  
  
1.  Mediante la copia desea actualizar, ábralo en la nueva versión. Se le aconsejará lo que la actualización no es reversible.  
  
2.  Una vez finalizada la actualización, cambie la ruta de acceso del programa externo a la nueva versión de devenv.exe. Haga clic en el nodo del proyecto en el **el Explorador de soluciones**, a continuación, elija **propiedades**. En el **depurar** pestaña, busque el cuadro de texto por **iniciar programa externo** y cambie la ruta de acceso de devenv.exe a la ruta de acceso de Visual Studio 2015, que debería ser algo parecido a esto:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Agregue una referencia a Microsoft.VisualStudio.Shell.14.0.dll. (Haga clic en el nodo del proyecto en el **el Explorador de soluciones** y, a continuación, elija **agregar / Reference**. Seleccione el **extensiones** pestaña y, a continuación, comprobar **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Compile la solución. Los archivos compilados se implementan en:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nombre de autor\>\\< nombre del proyecto\>\\< versión del proyecto\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para actualizar un proyecto de extensibilidad a los ensamblados de referencia de NuGet SDK de VS  
  
1.  Determine su proyecto necesita los ensamblados de referencia de SDK de VS.  En **el Explorador de soluciones**, expanda el proyecto **referencias** nodo y revise la lista de referencias del proyecto.  Ensamblados de referencias de SDK de VS tendrá el prefijo **Microsoft.VisualStudio** en el nombre (por ejemplo: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Quitar los ensamblados de referencia de SDK de VS seleccionándolos del proyecto, haga clic y **quitar**.  
  
3.  Agregue las versiones de NuGet de los ensamblados de referencia de SDK de VS.  Mientras sigue en la **referencias del explorador de soluciones** nodo, abra el **administrar paquetes NuGet...** cuadro de diálogo.  Si desea obtener más información sobre este cuadro de diálogo, vea [administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog). Los ensamblados de referencia de SDK de VS se publican en [nuget.org](http://www.nuget.org) por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Uso de **nuget.org** como su **origen del paquete**, busque el nombre del paquete NuGet que coincide con el ensamblado de referencia deseado (por ejemplo: Microsoft.VisualStudio.Shell.14.0) e instálelo en su proyecto.  NuGet puede agregar varios ensamblados de referencia con el fin de satisfacer las dependencias del ensamblado inicial.  
  
     Si lo prefiere, puede agregar a la vez todos los ensamblados de referencia de SDK de VS al instalar el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  También puede cambiar al uso de la versión de NuGet de las herramientas de compilación del SDK de VS. Este paquete de NuGet es [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) y una vez agregada a su proyecto se incluyen las herramientas necesarias y archivos para que pueda crear el proyecto de extensibilidad en un equipo sin instalado el SDK de VS de destino.  
  
> [!NOTE]
>  No es necesario que actualice sus proyectos de extensibilidad existentes para usar las herramientas y ensamblados de referencia de NuGet.  Podrán seguir compilar con los ensamblados de referencia y las herramientas instaladas con el SDK de VS.

