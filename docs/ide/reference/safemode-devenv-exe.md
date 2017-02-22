---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/SafeMode (modificador para Devenv)"
  - "Devenv, /SafeMode (modificador)"
  - "SafeMode (modificador)"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando únicamente el entorno y los servicios predeterminados.  
  
## Sintaxis  
  
```  
devenv /SafeMode   
```  
  
## Comentarios  
 Este modificador evita que se carguen VSPackages de otros fabricantes cuando se inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], garantizando así una ejecución estable.  
  
## Descripción  
 El ejemplo siguiente inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro.  
  
## Código  
  
```  
Devenv.exe /SafeMode  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)