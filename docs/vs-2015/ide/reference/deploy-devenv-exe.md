---
title: -Deploy (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4bed834524c159d42b2193857c805fab7628fe0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566790"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [-implementar (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/deploy-devenv-exe).  
  
  
Implementa una solución después de una compilación o recompilación. Solo se aplica a los proyectos de código administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## <a name="arguments"></a>Argumentos  
 `SolnConfigName`  
 Requerido. El nombre de la configuración de solución que se usará para compilar la solución mencionada en `SolutionName`.  
  
 `SolutionName`  
 Requerido. Ruta de acceso completa y nombre del archivo de solución.  
  
 /project `ProjName`  
 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.  
  
 /projectconfig `ProjConfigName`  
 Opcional. El nombre de una configuración de compilación de proyecto que se usará para crear el `/project` mencionado.  
  
## <a name="remarks"></a>Comentarios  
 El proyecto especificado debe ser un proyecto de implementación. Si el proyecto especificado no es un proyecto de implementación, se producirá un error cuando se pase el proyecto que se ha compilado para implementarse.  
  
 Escriba las cadenas que incluyen espacios entre comillas dobles.  
  
 Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo implementa el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Release` en la configuración de solución `Release` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



