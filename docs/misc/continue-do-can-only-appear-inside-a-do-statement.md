---
title: "&#39;Continue Do&#39; &#250;nicamente puede aparecer dentro de una instrucci&#243;n &#39;Do&#39; | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue Do&#39; &#250;nicamente puede aparecer dentro de una instrucci&#243;n &#39;Do&#39;
Una instrucción `Continue Do` solo puede aparecer dentro de un bucle `Do...Loop`.  
  
 **Id. de error:** BC30782  
  
### Para corregir este error  
  
1.  Si la instrucción `Continue Do` está en un bucle `For...Next`, cambie la instrucción a `Continue For`.  
  
2.  Si la instrucción `Continue Do` está en un bucle `While...End While`, cambie la instrucción a `Continue While`.  
  
3.  De lo contrario, quite la instrucción `Continue Do`.  
  
## Vea también  
 [Continue \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)