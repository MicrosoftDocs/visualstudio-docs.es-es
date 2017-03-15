---
title: "Error del compilador CS0744 | Microsoft Docs"
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
  - "CS0744"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0744"
ms.assetid: 7ce430d6-737a-4103-9116-d9a4a69f8af3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0744
Se esperaba la palabra clave contextual 'equals'  
  
 El patrón de una cláusula `join` es `join`...`in`...`on`...`equals`, como se muestra en este ejemplo:  
  
```  
var query = from x in array1 join y in array2 on x equals y select x;  
```  
  
### Para corregir este error  
  
1.  Agregue la palabra clave `equals` a la cláusula `join`.  
  
## Ejemplo  
 El código siguiente genera el error CS0744:  
  
```  
// cs0744.cs using System; using System.Linq; public class C { public static int Main() { int[] array1 = { 1, 2, 3 ,4, 5, 6,}; int[] array2 = { 5, 6, 7, 8, 9 }; var c = from x in array1 join y in array2 on x y // CS0744 select x; return 1; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [join \(cláusula\)](/dotnet/csharp/language-reference/keywords/join-clause)