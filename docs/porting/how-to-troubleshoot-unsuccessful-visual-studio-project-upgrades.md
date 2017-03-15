---
title: "C&#243;mo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "actualización de aplicaciones, Visual Studio"
  - "actualizar proyectos [Visual Studio]"
  - "proyectos, [Visual Studio], actualización"
  - "Asistente para conversión de Visual Studio"
  - "Asistente para conversión"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# C&#243;mo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A veces, Visual Studio no puede convertir totalmente un proyecto de una versión anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si las sugerencias en las secciones siguientes no resuelven un problema específico, es posible que pueda encontrar más información en la [wiki de TechNet: Portal de desarrollo](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## El proyecto no se ejecuta porque no se encuentran los archivos  
 Un archivo de proyecto contiene rutas de acceso codificadas de forma rígida que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza para ejecutar el proyecto al presionar F5.  Estas rutas pueden incluir la ubicación de devenv.exe y otros archivos necesarios.  En una versión actualizada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], las rutas de acceso de estos archivos pueden haber cambiado.  
  
#### Para resolver rutas de archivo incorrectas  
  
1.  Abra el archivo del proyecto en un editor de texto.  
  
2.  Examine las rutas de acceso que puedan ser incorrectas, sobre todo aquellas que contienen un número de versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Modifique las rutas de archivo incorrectas para que apunten a los nuevos destinos.  
  
## El proyecto no se compila porque las referencias no son válidas  
 Al actualizar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], también podría estar actualizando la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Si el proyecto contiene referencias desudadas en la versión más reciente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], quizá no se resuelvan correctamente.  Esto es especialmente probable en el caso de referencias que incluyen números de versión, por ejemplo, `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Si el código tiene muchas referencias no válidas, la solución más fácil podría ser utilizar la característica de compatibilidad con múltiples versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para tomar como destino una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Para resolver referencias incorrectas  
  
1.  Abra el archivo del proyecto en un editor de texto.  
  
2.  Abra las propiedades del proyecto.  
  
3.  Seleccione el valor correcto de **Versión de .NET Framework de destino**.  Como alternativa, puede modificar el valor de `<TargetFrameworkVersion>` directamente en el archivo de proyecto.  
  
 Si desea que el proyecto se ejecute en la versión actualizada de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], debe actualizar las referencias del proyecto, así como cualquier instrucción `Imports` o `Using` que llame a las referencias.  Si el proyecto se carga en el IDE, puede actualizar las referencias mediante el **Explorador de soluciones** o el cuadro de diálogo **Administrador de referencias**.  
  
## Vea también  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)