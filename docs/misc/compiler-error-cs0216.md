---
title: "Error del compilador CS0216 | Microsoft Docs"
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
  - "CS0216"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0216"
ms.assetid: afb3dd29-3eff-4b62-8267-eb726c2bcee4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0216
El operador 'operator' requiere que también se defina un operador coincidente 'missing\_operator'.  
  
 El operador [true](/dotnet/csharp/language-reference/keywords/true) definido por el usuario requiere un operador [false](/dotnet/csharp/language-reference/keywords/false) definido por el usuario y viceversa. Para obtener más información, consulta [Operadores](/dotnet/csharp/programming-guide/statements-expressions-operators/operators).  
  
 El ejemplo siguiente genera la advertencia CS0216:  
  
```  
// CS0216.cs class MyClass { public static bool operator true (MyClass MyInt)   // CS0216 { return true; } // to resolve, uncomment the following operator definition /* public static bool operator false (MyClass MyInt) { return true; } */ public static void Main() { } }  
```