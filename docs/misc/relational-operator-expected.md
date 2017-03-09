---
title: "Se esperaba un operador relacional | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba un operador relacional
Una instrucción `Case` contiene una cláusula `Is`, pero ningún operador de comparación como `=` o `>`. Si una instrucción `Case` no incluye un operador, `=` se supone y no se utiliza `Is`.  
  
 **Id. de error:** BC30239  
  
### Para corregir este error  
  
-   Quite la palabra clave `Is` o incluya a continuación un operador de comparación.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Operadores de comparación](/dotnet/visual-basic/language-reference/operators/comparison-operators)