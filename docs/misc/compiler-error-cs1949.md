---
title: "Error del compilador CS1949 | Microsoft Docs"
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
  - "CS1949"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1949"
ms.assetid: 959f553e-ac3d-43a1-b0a0-11e270f2ad64
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1949
La palabra clave contextual 'var' no se puede usar en una declaración de variable de rango.  
  
 El compilador aplica implícitamente un tipo a una variable de rango. No es necesario usar [var](/dotnet/csharp/language-reference/keywords/var) con una variable de rango.  
  
### Para corregir este error  
  
1.  Quite la palabra clave `var`  de delante de la variable de rango.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1949:  
  
```  
// cs1949.cs using System; using System.Linq; class Test { static void Main() { var x = from var i in Enumerable.Range(1, 100) // CS1949 select i; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)