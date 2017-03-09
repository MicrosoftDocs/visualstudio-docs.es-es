---
title: "Error del compilador CS0157 | Microsoft Docs"
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
  - "CS0157"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0157"
ms.assetid: a5d9d506-81f8-47dd-85b6-85f8170bcbef
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0157
El control no puede salir del texto de una cláusula finally  
  
 Todas las instrucciones de una cláusula [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally) deben ejecutarse. Para más información, vea [Instrucciones para el control de excepciones](/dotnet/csharp/language-reference/keywords/exception-handling-statements) y [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 El ejemplo siguiente genera la advertencia CS0157:  
  
```  
// CS0157.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } finally { return;   // CS0157, cannot leave finally clause } } } }  
```