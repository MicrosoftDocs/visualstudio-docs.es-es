---
title: "Error del compilador CS0742 | Microsoft Docs"
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
  - "CS0742"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0742"
ms.assetid: 078ee7af-17e4-4572-8fee-d97e09c9002b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0742
El cuerpo de una consulta debe terminar con una cláusula select o group  
  
 Una expresión de consulta debe finalizar con una cláusula `select` o con una cláusula `group` sin continuación.  
  
### Para corregir este error  
  
1.  Agregue la cláusula [select](/dotnet/csharp/language-reference/keywords/select-clause) o [group](/dotnet/csharp/language-reference/keywords/group-clause) a la consulta.  
  
## Ejemplo  
 El código siguiente genera el error CS0742:  
  
```  
// cs0742.cs using System.Linq; public class Test { public static int Main() { int[] array = { 1, 2, 3 }; var query = from num in array; // CS0742 return 1; } }  
```  
  
 Si la cláusula `group` usa la palabra clave [into](/dotnet/csharp/language-reference/keywords/into) para almacenar los resultados de la agrupación en un identificador temporal, no puede ser la última cláusula de una consulta. Seguirá siendo necesaria una segunda cláusula `select` o `group`.  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)