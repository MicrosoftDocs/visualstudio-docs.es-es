---
title: "Error del compilador CS1947 | Microsoft Docs"
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
  - "CS1947"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1947"
ms.assetid: e2822fba-a176-4466-9cdc-63c44e22ebcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1947
La variable de rango 'variable name' no puede asignarse; es de solo lectura.  
  
 Una variable de rango es como una variable de iteración en una instrucción `foreach`. No puede asignarse en una expresión de consulta.  
  
### Para corregir este error  
  
1.  Quite la asignación a la variable de rango.  
  
2.  Si es necesario, incluya una nueva variable de rango mediante la cláusula `let` y úsela para almacenar el valor.  
  
## Ejemplo  
 El código siguiente genera el error CS1947:  
  
```  
// cs1947.cs using System.Linq; class Test { static void Main() { int[] array = new int[] { 1, 2, 3, 4, 5 }; var x = from i in array let k = i select i = 5; // CS1947 x.ToList(); } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)