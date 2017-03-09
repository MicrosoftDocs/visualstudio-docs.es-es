---
title: "Las instrucciones &#39;SyncLock&#39; no son v&#225;lidas en la ventana Inmediato. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30135"
  - "bc30135"
helpviewer_keywords: 
  - "BC30135"
ms.assetid: 099771a1-5bf4-4c16-8fc3-262926c771df
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;SyncLock&#39; no son v&#225;lidas en la ventana Inmediato.
La instrucción `SyncLock` sincroniza los subprocesos y no está permitida en un contexto de depuración.  
  
 **Identificador de error:** BC30135  
  
### Para corregir este error  
  
-   No emita la instrucción `SyncLock` en la ventana **Inmediato**.  
  
## Vea también  
 [Ventana Inmediato](../ide/reference/immediate-window.md)   
 [SyncLock \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/synclock-statement)