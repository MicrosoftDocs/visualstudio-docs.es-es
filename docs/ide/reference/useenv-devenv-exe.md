---
title: -UseEnv (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 03d1bbe55ed1b355742f9cd2d3dedc1b66812bbc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)
Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y carga las variables de entorno en el cuadro de diálogo **Directorios de VC++**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Devenv /useenv  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y se cargan las variables de entorno en el cuadro de diálogo **Directorios de VC++**.  
  
```  
Devenv.exe /useenv  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)