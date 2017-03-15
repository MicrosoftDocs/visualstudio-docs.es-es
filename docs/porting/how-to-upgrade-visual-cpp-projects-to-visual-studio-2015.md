---
title: "C&#243;mo: Actualizar proyectos de Visual C++ a Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proyectos [C++], actualización"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Actualizar proyectos de Visual C++ a Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se abre por primera vez un proyecto de Visual C\+\+ creado en una versión anterior de Visual Studio, se le puede pedir que actualice el proyecto. El mensaje pregunta si desea actualizar el proyecto a la versión más reciente del compilador y las bibliotecas de Visual C\+\+. Las opciones de actualización dependen de la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se utilizó para crear el proyecto.  
  
 Puede usar [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] para abrir, editar y compilar proyectos de [!INCLUDE[win8](../debugger/includes/win8_md.md)] creados en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], pero para crear un nuevo proyecto de [!INCLUDE[win8](../debugger/includes/win8_md.md)] debe usar [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. \(Para crear un proyecto de [!INCLUDE[win81](../debugger/includes/win81_md.md)], debe usar [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]\).  
  
 Para crear un proyecto de Windows 10, debe usar [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)].  
  
 Si no se le pide que actualice el proyecto, es posible que no tenga que hacer nada para actualizarlo. Para obtener más información, consulta [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Si el proyecto \(.vcproj\) se creó en una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que es anterior a [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], debe actualizar el proyecto.  
  
-   Si el proyecto \(.vcxproj\) se creó en[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], tiene dos opciones:  
  
    -   Puede omitir la actualización.[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] cargará el proyecto sin realizar ningún cambio si tiene acceso a las herramientas de Visual C\+\+ en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] con SP1, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]. Puede proporcionar este acceso instalando la versión de Visual Studio con la que se creó el proyecto en el mismo equipo que tiene [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]. Para obtener más información, consulta [Instalar distintas versiones de Visual Studio en paralelo](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   Puede actualizar el proyecto permitiendo que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] realice los cambios que se describen más adelante en este tema. Si tiene más de un proyecto de Visual C\+\+ en la solución, debe actualizar todos.  
  
        > [!NOTE]
        >  Si rechaza la actualización la primera vez que se le solicita, puede actualizar el proyecto más adelante eligiendo **Actualizar proyecto de VC\+\+** en el menú **Proyecto**. Si el comando no aparece, no es necesario realizar ninguna actualización.  
  
## Actualizar un proyecto de Visual C\+\+  
 Si permite que [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] actualice el proyecto automáticamente, se realizarán los cambios siguientes:  
  
-   Cambia el proyecto para que use el compilador y las bibliotecas de [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] \(PlatformToolset \= VisualStudio v140\).  
  
-   En el caso de proyectos de [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)], cambia TargetFrameworkVersion a .NET Framework 4.5.2.  
  
## Seguir trabajando con un valor de PlatformToolset personalizado  
 Si desea seguir trabajando con un valor de PlatformToolset personalizado en [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)], el conjunto de herramientas debe estar en %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ en un equipo x86 o en %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ si se trata de un equipo x64. Para obtener información sobre cómo crear un valor de PlatformToolset personalizado, vea [Compatibilidad nativa con múltiples versiones \(multi\-targeting\) de C\+\+](http://go.microsoft.com/fwlink/?LinkId=248587) en el blog del equipo de Visual C\+\+.  
  
## Vea también  
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)