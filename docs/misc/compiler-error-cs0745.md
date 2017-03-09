---
title: "Error del compilador CS0745 | Microsoft Docs"
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
  - "CS0745"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0745"
ms.assetid: 6ae77eb2-a940-43aa-a198-3042d144613a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0745
Se esperaba la palabra clave contextual 'by'  
  
 El patrón de la cláusula `group` es `group...by` seguido de un elemento opcional `into`, como se muestra en el ejemplo siguiente:  
  
```  
string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name by name[0];  
```  
  
 o  
  
```  
var query2 = from name in names group name by name[0] into g //...additional query clauses  
```  
  
### Para corregir este error  
  
1.  Agregue la palabra clave `by` a la cláusula `group`.  
  
## Ejemplo  
 El código siguiente genera el error CS0745:  
  
```  
// cs0745.cs using System; using System.Linq; public class C { public static int Main() { string[] names = { "Bob", "Bill", "Jonetta", "Mary" }; var query = from name in names group name name[0]; // CS0745 return 1; } }  
```  
  
## Vea también  
 [Expresiones de consulta LINQ](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [group \(cláusula\)](/dotnet/csharp/language-reference/keywords/group-clause)