---
title: "Error del compilador CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0215
El tipo de valor devuelto del operador True o False debe ser bool  
  
 Los operadores [true](/dotnet/csharp/language-reference/keywords/true) y [false](/dotnet/csharp/language-reference/keywords/false) definidos por el usuario deben tener un tipo de valor devuelto de [bool](/dotnet/csharp/language-reference/keywords/bool). Para obtener más información, consulta [Operadores sobrecargables](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators).  
  
 El ejemplo siguiente genera la advertencia CS0215:  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```