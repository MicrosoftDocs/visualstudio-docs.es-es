---
title: "Error del compilador CS1940 | Microsoft Docs"
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
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1940
Se encontraron varias implementaciones del patrón de consulta para el tipo de origen 'tipo'. Llamada ambigua a 'método'.  
  
 Este error se genera cuando se definen varias implementaciones de un método de consulta y el compilador no puede eliminar la ambigüedad de cuál es la mejor para la consulta. En el ejemplo siguiente, las dos versiones de `Select` tienen la misma firma, ya que ambas aceptan un `int` como parámetro de entrada y `int` como valor devuelto.  
  
### Para corregir este error  
  
1.  Proporcione solo una implementación para cada método.  
  
## Ejemplo  
 El código siguiente genera el error CS1940:  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## Vea también  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)