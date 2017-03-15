---
title: "La construcci&#243;n &#39;End SyncLock&#39; debe ir precedida de la instrucci&#243;n &#39;SyncLock&#39; correspondiente | Microsoft Docs"
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
  - "vbc30674"
  - "bc30674"
helpviewer_keywords: 
  - "BC30674"
ms.assetid: 2d473b0b-ca9e-43b5-9bcb-b00766bc90a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La construcci&#243;n &#39;End SyncLock&#39; debe ir precedida de la instrucci&#243;n &#39;SyncLock&#39; correspondiente
Los bloques `SyncLock` comienzan con la palabra clave `SyncLock` y terminan con la construcción `End` `SyncLock`.  
  
 **Identificador de error:** BC30674  
  
### Para corregir este error  
  
-   Asegúrese de que el bloque `SyncLock` comienza con una instrucción `SyncLock`.  
  
## Vea también  
 [SyncLock \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/synclock-statement)