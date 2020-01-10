---
title: 'Cómo: solucionar problemas de actualizaciones de proyecto incorrectas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
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
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844450"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Cómo: Solucionar problemas de actualizaciones de proyecto de Visual Studio incorrectas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A veces, Visual Studio no puede convertir totalmente un proyecto de una versión anterior de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si las sugerencias de las secciones siguientes no resuelven su problema específico, es posible que pueda encontrar más información en TechNet [wiki: portal de desarrollo](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>El proyecto no se ejecuta porque no se encuentran los archivos
 Un archivo de proyecto contiene rutas de acceso codificadas de forma rígida que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utiliza para ejecutar el proyecto al presionar F5. Estas rutas pueden incluir la ubicación de devenv.exe y otros archivos necesarios. En una versión actualizada de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], las rutas de acceso de estos archivos pueden haber cambiado.

#### <a name="to-resolve-incorrect-file-paths"></a>Para resolver rutas de archivo incorrectas

1. Abra el archivo del proyecto en un editor de texto.

2. Examine las rutas de acceso que puedan ser incorrectas, sobre todo aquellas que contienen un número de versión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

3. Modifique las rutas de archivo incorrectas para que apunten a los nuevos destinos.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>El proyecto no se compila porque las referencias no son válidas
 Al actualizar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], también podría estar actualizando la versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Si el proyecto contiene referencias desudadas en la versión más reciente de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], quizá no se resuelvan correctamente. Esto es especialmente probable en el caso de referencias que incluyen números de versión, por ejemplo, `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Si el código tiene muchas referencias no válidas, la solución más fácil podría ser utilizar la característica de compatibilidad con múltiples versiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para tomar como destino una versión anterior de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Para resolver referencias incorrectas

1. Abra el archivo del proyecto en un editor de texto.

2. Abra las propiedades del proyecto.

3. Seleccione el valor correcto de **Plataforma de destino**. Como alternativa, puede modificar el valor de `<TargetFrameworkVersion>` directamente en el archivo de proyecto.

   Si desea que el proyecto se ejecute en la versión actualizada de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], debe actualizar las referencias del proyecto, así como cualquier instrucción `Imports` o `Using` que llame a las referencias. Si el proyecto se carga en el IDE, puede actualizar las referencias mediante el **Explorador de soluciones** o el cuadro de diálogo **Administrador de referencias**.

## <a name="see-also"></a>Vea también
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [convertir a ASP.net 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
