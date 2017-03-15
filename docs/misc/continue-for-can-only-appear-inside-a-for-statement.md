---
title: "&#39;Continue For&#39; &#250;nicamente puede aparecer dentro de una instrucci&#243;n &#39;For&#39; | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue For&#39; &#250;nicamente puede aparecer dentro de una instrucci&#243;n &#39;For&#39;
Una instrucción `Continue For` solo puede aparecer dentro de un bucle `For...Next`.  
  
 **Identificador de error:** BC30783  
  
### Para corregir este error  
  
1.  Si la instrucción `Continue For` está en `Do...Loop`, cambie la instrucción a `Continue Do`.  
  
     \-O bien\-  
  
     Si la instrucción `Continue For` está en un bucle `While...End While`, cambie la instrucción a `Continue While`.  
  
2.  De lo contrario, quite la instrucción `Continue For`.  
  
## Vea también  
 [Continue \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)