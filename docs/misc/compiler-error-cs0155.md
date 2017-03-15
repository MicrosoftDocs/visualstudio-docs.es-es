---
title: "Error del compilador CS0155 | Microsoft Docs"
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
  - "CS0155"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0155"
ms.assetid: 6c92984a-2b10-453e-9cb7-e6a1d1b98aa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0155
El tipo detectado o producido debe derivarse de System.Exception  
  
 Se intentó pasar un tipo de datos que no se deriva de **System.Exception** en un bloque [catch](/dotnet/csharp/language-reference/keywords/try-catch). Solo los tipos de datos que se derivan de **System.Exception** se pueden pasar a un bloque **catch**. Para más información, vea [Instrucciones para el control de excepciones](/dotnet/csharp/language-reference/keywords/exception-handling-statements) y [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 El ejemplo siguiente genera la advertencia CS0155:  
  
```  
// CS0155.cs using System; namespace MyNamespace { public class MyClass2 // try the following line instead // public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } catch (MyClass2)   // CS0155, resolves if you derive MyClass2 from Exception { } } } }  
```