---
title: "&#39;Case&#39; no puede seguir a &#39;Case Else&#39; en la misma instrucci&#243;n &#39;Select&#39; | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; no puede seguir a &#39;Case Else&#39; en la misma instrucci&#243;n &#39;Select&#39;
Una instrucción `Case Else` presenta las instrucciones que se ejecutarán si se encuentra ninguna coincidencia para la instrucción `Case` inicial. Se encontró una instrucción `Case` después de una instrucción `Case Else` en el mismo bloque `Select`.  
  
 **Identificador de error:** BC30321  
  
### Para corregir este error  
  
-   Mueva la instrucción `Case Else` a la ubicación adecuada después de la instrucción `Case`.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)