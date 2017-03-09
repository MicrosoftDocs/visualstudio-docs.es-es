---
title: "&#39;Case Else&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case Else&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select Case&#39;
Una instrucción `Case Else` aparece fuera de un bloque `Select`. Una instrucción `Case Else` solo se puede usar entre una instrucción `Select` o `Select Case` y su instrucción `End Select` correspondiente.  
  
 **Identificador de error:** BC30071  
  
### Para corregir este error  
  
-   Quite la instrucción `Case Else` o muévala a un bloque `Select`.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)