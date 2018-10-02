---
title: 'Cómo: solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 9cd9ca350fe238c0c15998cbc44ca3e8236890b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574032"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A veces, Visual Studio no puede convertir totalmente un proyecto de una versión anterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si las sugerencias en las secciones siguientes no resuelven el problema específico, es posible que pueda encontrar más información en el TechNet [Wiki: Portal de desarrollo](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## <a name="the-project-does-not-run-because-files-are-not-found"></a>El proyecto no se ejecuta porque no se encuentran los archivos  
 Un archivo de proyecto contiene rutas de acceso codificadas de forma rígida que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliza para ejecutar el proyecto al presionar F5. Estas rutas pueden incluir la ubicación de devenv.exe y otros archivos necesarios. En una versión actualizada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], las rutas de acceso de estos archivos pueden haber cambiado.  
  
#### <a name="to-resolve-incorrect-file-paths"></a>Para resolver rutas de archivo incorrectas  
  
1.  Abra el archivo del proyecto en un editor de texto.  
  
2.  Examine las rutas de acceso que puedan ser incorrectas, sobre todo aquellas que contienen un número de versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Modifique las rutas de archivo incorrectas para que apunten a los nuevos destinos.  
  
## <a name="the-project-does-not-build-because-references-are-not-valid"></a>El proyecto no se compila porque las referencias no son válidas  
 Al actualizar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], también podría estar actualizando la versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Si el proyecto contiene referencias desudadas en la versión más reciente de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], quizá no se resuelvan correctamente. Esto es especialmente probable en el caso de referencias que incluyen números de versión, por ejemplo, `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Si el código tiene muchas referencias no válidas, la solución más fácil podría ser utilizar la característica de compatibilidad con múltiples versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para tomar como destino una versión anterior de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
#### <a name="to-resolve-incorrect-references"></a>Para resolver referencias incorrectas  
  
1.  Abra el archivo del proyecto en un editor de texto.  
  
2.  Abra las propiedades del proyecto.  
  
3.  Seleccione el valor correcto **.NET Framework de destino** valor. Como alternativa, puede modificar el valor de `<TargetFrameworkVersion>` directamente en el archivo de proyecto.  
  
 Si desea que el proyecto se ejecute en la versión actualizada de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], debe actualizar las referencias del proyecto, así como cualquier instrucción `Imports` o `Using` que llame a las referencias. Si el proyecto se carga en el IDE, puede actualizar las referencias mediante **el Explorador de soluciones** o **Administrador de referencias** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [/Upgrade (devenv.exe)](../ide/reference/upgrade-devenv-exe.md)   
 [Convertir a ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)

