---
title: "Advertencia del compilador (nivel 2) CS0458 | Microsoft Docs"
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
  - "CS0458"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0458"
ms.assetid: 0986c620-b4bc-4e4b-976f-88359cfa3a45
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0458
El resultado de la expresión siempre es 'null' del tipo 'type name'  
  
 Esta advertencia se produce debido a una expresión `nullable` cuyo resultado es siempre `null`.  
  
 El código siguiente genera la advertencia CS0458.  
  
## Ejemplo  
 Este ejemplo ilustra algunas de las distintas operaciones con los tipos `nullable` que producirán este error.  
  
```  
// CS0458.cs using System; public  class Test { public static void Main() { int a = 5; int? b = a + null;    // CS0458 int? qa = 15; b = qa + null;        // CS0458 b -= null;            // CS0458 int? qa2 = null; b = qa2 + null;       // CS0458 qa2 -= null;          // CS0458 } }  
```