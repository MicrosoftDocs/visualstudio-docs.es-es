---
title: "C&#243;mo: migrar proyectos de extensibilidad en Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, actualizar"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: migrar proyectos de extensibilidad en Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A continuación le mostramos cómo actualizar la extensión.  
  
> [!IMPORTANT]
>  Si desea mantener una versión de la solución de extensión para una versión anterior de Visual Studio, asegúrese de hacer una copia antes de actualizarlo. Puede ser difícil volver a la versión actualizada a su estado anterior.  
  
#### Para actualizar una solución de extensibilidad  
  
1.  Con la copia que desea actualizar, ábralo en la nueva versión. Se recomienda que la actualización no es reversible.  
  
2.  Una vez completada la actualización, puede cambiar la ruta de acceso del programa externo a la nueva versión de devenv.exe. Haga clic en el nodo del proyecto en el **el Explorador de soluciones**, a continuación, elija **propiedades**. En el **Depurar** ficha, busque el cuadro de texto por **programa externo de inicio** y cambie la ruta de acceso de devenv.exe a la ruta de acceso de Visual Studio 2015, que debe ser similar a esto:  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  Agregue una referencia a Microsoft.VisualStudio.Shell.14.0.dll. \(Haga clic en el nodo del proyecto en el **el Explorador de soluciones** y, a continuación, elija **Agregar \/ Reference**. Seleccione el **extensiones** ficha y, a continuación, comprobar **Microsoft.VisualStudio.Shell.14.0**.\)  
  
4.  Compile la solución. Los archivos generados se implementan en:  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< nombre del autor \> \\ \< nombre del proyecto \> \\ \< versión del proyecto \> \\**.  
  
#### Para actualizar un proyecto de extensibilidad a los ensamblados de referencia de SDK de VS de NuGet  
  
1.  Determinar los ensamblados de referencia de SDK de VS que su proyecto necesita.  En **el Explorador de soluciones**, expanda el proyecto **referencias** nodo y revise la lista de referencias del proyecto.  Ensamblados de referencias de SDK de VS tendrán el prefijo **Microsoft.VisualStudio** en el nombre \(por ejemplo: Microsoft.VisualStudio.Shell.14.0\).  
  
2.  Quitar los ensamblados de referencia de SDK de VS seleccionándolos del proyecto, haga clic y **quitar**.  
  
3.  Agregar las versiones de los ensamblados de referencia de SDK de VS de NuGet.  Mientras sigue en la **referencias del explorador de soluciones** nodo, abra el **Administrar paquetes de NuGet...** cuadro de diálogo.  Si desea obtener más información acerca de este cuadro de diálogo, vea [Administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog). Los ensamblados de referencia de SDK de VS se publican en [nuget.org](http://www.nuget.org) por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Usando **nuget.org** como su **origen del paquete**, busque el nombre del paquete NuGet que coincide con el ensamblado de referencia deseado \(por ejemplo: Microsoft.VisualStudio.Shell.14.0\) e instálelo en su proyecto.  NuGet puede agregar varios ensamblados de referencia para satisfacer las dependencias del ensamblado inicial.  
  
     Si lo prefiere, puede agregar todos los ensamblados de referencia de SDK de VS a la vez al instalar el SDK de VS [paquete Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  También puede cambiar a la versión de NuGet de las herramientas de generación de SDK de VS. Este paquete de NuGet es [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) y una vez agregado a su proyecto incluirá las herramientas necesarias y archivos para que pueda crear el proyecto de extensibilidad en un equipo sin instalado el SDK de VS de destino.  
  
> [!NOTE]
>  No es necesario que actualice los proyectos de extensibilidad existentes para usar herramientas y ensamblados de referencia de NuGet.  Puede seguir generar mediante los ensamblados de referencia y herramientas se instalan con el SDK de VS.