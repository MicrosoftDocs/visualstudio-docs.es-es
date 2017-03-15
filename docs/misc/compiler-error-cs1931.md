---
title: "Error del compilador CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1931
La variable de rango 'variable' entra en conflicto con una declaración anterior de 'variable'.  
  
 La declaración de una variable de rango, al igual que todas las demás declaraciones, debe tener un identificador que sea único dentro del espacio de declaración de la variable.  
  
### Para corregir este error  
  
1.  Asigne un nombre único a la variable de rango.  
  
## Ejemplo  
 El código siguiente genera el error CS1931 porque el identificador `x` se usa como una variable local en `Main` y como la variable de rango en la expresión de consulta:  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)