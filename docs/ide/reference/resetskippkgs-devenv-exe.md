---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs (modificador para Devenv)"
  - "Devenv, /ResetSkipPkgs (modificador)"
  - "ResetSkipPkgs (modificador)"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Borra todas las opciones a fin de omitir la carga agregada a VSPackages por aquellos usuarios que desean evitar el problema de carga de VSPackages; a continuación, inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintaxis  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## Comentarios  
 La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage; borrar la etiqueta vuelve a habilitarla.  
  
## Ejemplo  
 El ejemplo siguiente borra todas las etiquetas SkipLoading.  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)