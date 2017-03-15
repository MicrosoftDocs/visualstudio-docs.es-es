---
title: "Error del compilador CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0835
No se puede convertir una expresión lambda a un árbol de expresión cuyo argumento de tipo 'tipo' no sea un tipo delegado.  
  
 Si una expresión lambda se convierte a un árbol de expresión, dicho árbol debe tener un tipo delegado para su argumento. Además, la expresión lambda debe poder convertirse al tipo delegado.  
  
### Para corregir este error  
  
1.  Cambie el parámetro de tipo de `int` a un tipo delegado, por ejemplo: `Func<int,int>`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0835:  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```