---
title: "Las instrucciones &#39;On Error&#39; no son v&#225;lidas dentro de instrucciones &#39;SyncLock&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;On Error&#39; no son v&#225;lidas dentro de instrucciones &#39;SyncLock&#39;
Las instrucciones `On Error` no se pueden usar en bloques `SyncLock` porque afectarían a la sincronización de subprocesos.  
  
 **Identificador de error:** BC30752  
  
### Para corregir este error  
  
1.  Coloque las instrucciones `On Error` fuera de los bloques `SyncLock`.  
  
## Vea también  
 [On Error \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/on-error-statement)