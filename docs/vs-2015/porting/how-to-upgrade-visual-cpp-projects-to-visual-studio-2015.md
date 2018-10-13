---
title: 'Cómo: actualizar proyectos de Visual C++ a Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8673d2d1648acad973ebfa339e0334a5c1fd769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188576"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Cómo: Actualizar proyectos de Visual C++ a Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [Visual C++ Guía de migración y actualización](https://docs.microsoft.com/en-us/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Cuando se abre por primera vez un proyecto de Visual C++ creado en una versión anterior de Visual Studio, se le puede pedir que actualice el proyecto. El mensaje pregunta si desea actualizar el proyecto a la versión más reciente del compilador y las bibliotecas de Visual C++. Las opciones de actualización dependen de la versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que se utilizó para crear el proyecto.  
  
 Puede usar [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] para abrir, editar y compilar proyectos de [!INCLUDE[win8](../includes/win8-md.md)] creados en [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], pero para crear un nuevo proyecto de [!INCLUDE[win8](../includes/win8-md.md)] debe usar [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Para crear un proyecto de [!INCLUDE[win81](../includes/win81-md.md)], debe usar [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]).  
  
 Para crear un proyecto de Windows 10, debe usar [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].  
  
 Si no se le pide que actualice el proyecto, es posible que no tenga que hacer nada para actualizarlo.  
  
-   Si el proyecto (.vcproj) se creó en una versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que es anterior a [!INCLUDE[vs2010](../includes/vs2010-md.md)], debe actualizar el proyecto.  
  
-   Si el proyecto (.vcxproj) se creó en[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], tiene dos opciones:  
  
    -   Puede omitir la actualización. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] cargará el proyecto sin realizar ningún cambio si tiene acceso a las herramientas de Visual C++ en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] con SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Puede proporcionar este acceso instalando la versión de Visual Studio con la que se creó el proyecto en el mismo equipo que tiene [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Para obtener más información, consulta [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).  
  
    -   Puede actualizar el proyecto permitiendo que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] realice los cambios que se describen más adelante en este tema. Si tiene más de un proyecto de Visual C++ en la solución, debe actualizar todos.  
  
        > [!NOTE]
        >  Si rechaza la actualización la primera vez que se le solicita, puede actualizar el proyecto más adelante eligiendo **Actualizar proyecto de VC++** en el menú **Proyecto** . Si el comando no aparece, no es necesario realizar ninguna actualización.  
  
## <a name="upgrading-a-visual-c-project"></a>Actualizar un proyecto de Visual C++  
 Si permite que [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] actualice el proyecto automáticamente, se realizarán los cambios siguientes:  
  
-   Cambia el proyecto para que use el compilador y las bibliotecas de [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] (PlatformToolset = VisualStudio v140).  
  
-   En el caso de proyectos de [!INCLUDE[cppcli](../includes/cppcli-md.md)] , cambia TargetFrameworkVersion a .NET Framework 4.5.2.  
  
## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Seguir trabajando con un valor de PlatformToolset personalizado  
 Si desea seguir trabajando con un valor de PlatformToolset personalizado en [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], el conjunto de herramientas debe estar en %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ en un equipo x86 o en %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ si se trata de un equipo x64. Para obtener información sobre cómo crear un valor de PlatformToolset personalizado, vea [Compatibilidad nativa con múltiples versiones (multi-targeting) de C++](http://go.microsoft.com/fwlink/?LinkId=248587) en el blog del equipo de Visual C++.  
  
## <a name="see-also"></a>Vea también  
 [Guía de migración y actualización de Visual C++](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)   
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)

