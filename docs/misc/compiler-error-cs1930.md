---
title: "Error del compilador CS1930 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1930
Ya se ha declarado la variable de rango 'name'  
  
 La variable de rango de una expresión de consulta está en ámbito hasta que finaliza la expresión de la consulta. Por lo tanto, debe tener un identificador único.  
  
### Para corregir este error  
  
1.  Asigne un nombre único a cada variable de rango que se introduce en una expresión de consulta.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1930 porque el identificador `num` se usa para la variable de rango en la cláusula `from` y para la variable de rango que introduce la cláusula `let`.  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)