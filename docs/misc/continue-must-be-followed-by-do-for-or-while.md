---
title: "La instrucci&#243;n &#39;Continue&#39; debe ir seguida de &#39;Do&#39;, &#39;For&#39; o &#39;While&#39; | Microsoft Docs"
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
  - "bc30781"
  - "vbc30781"
helpviewer_keywords: 
  - "BC30781"
ms.assetid: a0d5854d-ca44-4c6b-9458-4fc50d29281a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Continue&#39; debe ir seguida de &#39;Do&#39;, &#39;For&#39; o &#39;While&#39;
Una instrucción `Continue` debe ir seguida de `Do`, `For` o `While`, según si la instrucción `Continue` aparece dentro de un bucle `Do...Loop`, `For...Next` o `While...End While`.  
  
 **Id. de error:** BC30781  
  
### Para corregir este error  
  
1.  Si la instrucción `Continue` está en un bucle `Do...Loop`, cambie la instrucción a `Continue Do`.  
  
2.  Si la instrucción `Continue` está en un bucle `For...Next`, cambie la instrucción a `Continue For`.  
  
3.  Si la instrucción `Continue` está en un bucle `While...End While`, cambie la instrucción a `Continue While`.  
  
4.  De lo contrario, quite la instrucción `Continue`.  
  
## Vea también  
 [Continue \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/continue-statement)