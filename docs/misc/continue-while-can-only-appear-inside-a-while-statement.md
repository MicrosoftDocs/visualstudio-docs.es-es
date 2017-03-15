---
title: "&#39;Continue While&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;While&#39;. | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;While&#39;.
Una instrucción `Continue While` solo puede aparecer dentro de un bucle `For...Next`.  
  
 **Identificador de error:** BC30784  
  
### Para corregir este error  
  
1.  Si la instrucción `Continue While` está en un bucle `Do...Loop`, cambie la instrucción a `Continue Do`.  
  
2.  Si la instrucción `Continue While` está en un bucle `For...Next`, cambie la instrucción a `Continue For`.  
  
3.  En otras circunstancias, quite la instrucción `Continue While`.  
  
## Vea también  
 [Continue \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [While...End While \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)