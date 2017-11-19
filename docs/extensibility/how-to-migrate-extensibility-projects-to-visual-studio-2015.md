---
title: "Cómo: migrar proyectos de extensibilidad de Visual Studio 2015 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016e609acb7ad837580b4cabb6055169ac7357c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Cómo: migrar proyectos de extensibilidad de Visual Studio 2015
Aquí se muestra cómo actualizar la extensión.  
  
> [!IMPORTANT]
>  Si desea mantener una versión de la solución de extensión para una versión anterior de Visual Studio, asegúrese de realizar una copia antes de que la actualización. Puede resultar difícil devolver la versión actualizada a su estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para actualizar una solución de extensibilidad  
  
1.  Mediante la copia que desea actualizar, ábralo en la nueva versión. Se le aconsejará que la actualización no es reversible.  
  
2.  Una vez completada la actualización, cambie la ruta de acceso del programa externo a la nueva versión de devenv.exe. Haga clic en el nodo de proyecto en el **el Explorador de soluciones**, a continuación, elija **propiedades**. En el **depurar** ficha, busque el cuadro de texto por **programa externo de inicio** y cambie la ruta de acceso de devenv.exe a la ruta de acceso de Visual Studio 2015, que debe ser similar al siguiente:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Agregue una referencia a Microsoft.VisualStudio.Shell.14.0.dll. (Haga clic en el nodo de proyecto en el **el Explorador de soluciones** y, a continuación, elija **agregar / Reference**. Seleccione el **extensiones** ficha y, a continuación, comprobar **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Compile la solución. Los archivos generados se implementan en:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nombre de autor\>\\< nombre de proyecto\>\\< versión del proyecto\> \\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para actualizar un proyecto de extensibilidad para ensamblados de referencia de SDK de VS de NuGet  
  
1.  Determinar los ensamblados de referencia de SDK de VS que su proyecto necesite.  En **el Explorador de soluciones**, expanda el proyecto **referencias** nodo y revise la lista de referencias del proyecto.  Ensamblados de referencias del SDK de VS tendrán el prefijo **Microsoft.VisualStudio** en el nombre (por ejemplo: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Quitar los ensamblados de referencia de SDK de VS del proyecto por ello, selecciónelos, haga clic y **quitar**.  
  
3.  Agregue las versiones de NuGet de los ensamblados de referencia de SDK de VS.  Mientras sigue en la **referencias del explorador de soluciones** nodo, abra el **administrar paquetes de NuGet...**  cuadro de diálogo.  Si desea obtener más información sobre este cuadro de diálogo, vea [UI del Administrador de paquetes](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI). Se han publicado los ensamblados de referencia de SDK de VS en [nuget.org](http://www.nuget.org) por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Usar **nuget.org** como su **origen del paquete**, busque el nombre del paquete de NuGet que coincide con el ensamblado de referencia deseado (por ejemplo: Microsoft.VisualStudio.Shell.14.0) e instalarlo en su proyecto.  NuGet puede agregar varios ensamblados de referencia con el fin de satisfacer las dependencias del ensamblado inicial.  
  
     Si lo prefiere, puede agregar a la vez todos los ensamblados de referencia de SDK de VS al instalar el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  También puede cambiar a la versión de NuGet de las herramientas de compilación del SDK de VS. Este paquete de NuGet es [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) y una vez agregado a su proyecto se incluyen las herramientas que necesitan y archivos que le permite compilar el proyecto de extensibilidad en un equipo sin instalado el SDK de VS de destino.  
  
> [!NOTE]
>  No es necesario que actualice sus proyectos de extensibilidad existentes para usar ensamblados de referencia de NuGet y herramientas.  Puede continuar generar mediante ensamblados de referencia y herramientas se instalan con el SDK de VS.