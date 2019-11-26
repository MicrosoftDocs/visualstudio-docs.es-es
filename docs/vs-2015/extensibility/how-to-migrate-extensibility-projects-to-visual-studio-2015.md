---
title: 'Cómo: migrar proyectos de extensibilidad a Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b48370847cbb2cf8b171342aff9baf38c40a22
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295552"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Cómo: migrar proyectos de extensibilidad a Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aquí se muestra cómo actualizar la extensión.  
  
> [!IMPORTANT]
> Si tiene previsto mantener una versión de la solución de extensión para una versión anterior de Visual Studio, asegúrese de realizar una copia antes de actualizarla. Puede ser difícil devolver la versión actualizada a su estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para actualizar una solución de extensibilidad  
  
1. Con la copia que desea actualizar, ábrala en la nueva versión. Se le notificará que la actualización no es reversible.  
  
2. Una vez finalizada la actualización, cambie la ruta de acceso del programa externo a la nueva versión de devenv. exe. Haga clic con el botón secundario en el nodo del proyecto en el **Explorador de soluciones**y, a continuación, elija **propiedades**. En la pestaña **depurar** , busque el cuadro de texto por **programa externo de inicio** y cambie la ruta de devenv. exe a la ruta de acceso 2015 de Visual Studio, que debería tener un aspecto similar al siguiente:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. Agregue una referencia a Microsoft. VisualStudio. Shell. 14.0. dll. (Haga clic con el botón secundario en el nodo del proyecto en el **Explorador de soluciones** y, a continuación, elija **Agregar o referencia**. Seleccione la pestaña **extensiones** y, a continuación, Active **Microsoft. VisualStudio. Shell. 14.0**.  
  
4. Compile la solución. Los archivos compilados se implementan en:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nombre del autor\>\\< nombre del proyecto** \>\\< versión del proyecto\>\\.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para actualizar un proyecto de extensibilidad a los ensamblados de referencia de NuGet de VS SDK  
  
1. Determine los ensamblados de referencia del SDK de VS que necesita el proyecto.  En **Explorador de soluciones**, expanda el nodo **referencias** del proyecto y revise la lista de referencias del proyecto.  VS SDK References assemblies tendrá el prefijo **Microsoft. VisualStudio** en el nombre (por ejemplo: Microsoft. VisualStudio. Shell. 14.0).  
  
2. Quite los ensamblados de referencia del SDK de VS del proyecto seleccionándolos, haga clic con el botón derecho y **Quite**.  
  
3. Agregue las versiones de NuGet de los ensamblados de referencia del SDK de VS.  Mientras sigue en el nodo **referencias de explorador de soluciones** , Abra **la.** .  Si quiere obtener más información sobre este cuadro de diálogo, consulte [Administración de paquetes NuGet mediante el cuadro de diálogo](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio). Los ensamblados de referencia de VS SDK se publican en [Nuget.org](https://www.nuget.org/) por [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Con **Nuget.org** como el **origen del paquete**, busque el nombre del paquete Nuget que coincida con el ensamblado de referencia deseado (por ejemplo: Microsoft. VisualStudio. Shell. 14.0) e instálelo en el proyecto.  NuGet puede agregar varios ensamblados de referencia para satisfacer las dependencias del ensamblado inicial.  
  
     Si lo prefiere, puede Agregar todos los ensamblados de referencia del SDK de VS a la vez mediante la instalación del [paquete meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK de vs.  
  
5. También puede cambiar al uso de la versión de NuGet de las herramientas de compilación de VS SDK. Este paquete de NuGet es [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) y, una vez agregado al proyecto, incluirá las herramientas y los archivos de destino necesarios para crear el proyecto de extensibilidad en un equipo que no tenga instalado el SDK de vs.  
  
> [!NOTE]
> No es necesario actualizar los proyectos de extensibilidad existentes para usar herramientas y ensamblados de referencia de NuGet.  Pueden seguir compilando con los ensamblados de referencia y las herramientas que se instalan con el SDK de VS.
