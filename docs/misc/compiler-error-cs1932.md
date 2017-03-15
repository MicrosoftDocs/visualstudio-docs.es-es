---
title: "Error del compilador CS1932 | Microsoft Docs"
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
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1932
No se puede asignar 'expresión' a una variable de rango.  
  
 El compilador debe poder inferir el tipo de una variable de rango, si se introduce en una cláusula `from` o una cláusula `let`. No puede ser null porque null no es un tipo y no se puede asignar con una expresión de un tipo no seguro.  
  
### Para corregir este error  
  
-   Quite la asignación que no es válida.  
  
-   Convierta explícitamente la expresión a un tipo permitido.  
  
## Ejemplo  
 El código siguiente genera CS1932 porque no se puede inferir el tipo de la variable de rango. Convierta el valor al tipo deseado para solucionar el error, como se muestra en el ejemplo siguiente.  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)