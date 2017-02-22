---
title: "/UseEnv (devenv.exe) | Microsoft Docs"
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
  - "VC.Project.UseEnvVars.ExcludePath"
  - "VC.Project.UseEnvVars.LibraryPath"
  - "VC.Project.UseEnvVars.SourcePath"
  - "VC.Project.UseEnvVars.Include"
  - "VC.Project.UseEnvVars.Path"
  - "VC.Project.UseEnvVars.ReferencePath"
helpviewer_keywords: 
  - "/UseEnv (modificador para Devenv)"
  - "Devenv, /UseEnv"
  - "UseEnv (modificador)"
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /UseEnv (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y carga las variables de entorno en el cuadro de diálogo **Directorios de VC\+\+**.  
  
## Sintaxis  
  
```  
Devenv /useenv  
```  
  
## Ejemplo  
 El ejemplo siguiente inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y carga las variables de entorno en el cuadro de diálogo **Directorios de VC\+\+**.  
  
```  
Devenv.exe /useenv  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)