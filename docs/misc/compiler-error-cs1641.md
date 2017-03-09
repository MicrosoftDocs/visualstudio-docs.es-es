---
title: "Error del compilador CS1641 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1641"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1641"
ms.assetid: ba6eab47-c28b-4531-b6a0-6d538b236d19
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1641
Un campo de búfer de tamaño fijo debe tener el especificador de tamaño de matriz detrás del nombre de campo  
  
 A diferencia de las matrices normales, los búferes de tamaño fijo requieren que se especifique un tamaño constante en el punto de declaración. Para resolver este error, agregue un literal entero positivo o un entero positivo constante y coloque corchetes después del identificador.  
  
 El ejemplo siguiente genera la advertencia CS1641:  
  
```  
// CS1641.cs // compile with: /unsafe /target:library unsafe struct S { fixed int [] a;  // CS1641 // OK fixed int b [10]; const int c = 10; fixed int d [c]; }  
```