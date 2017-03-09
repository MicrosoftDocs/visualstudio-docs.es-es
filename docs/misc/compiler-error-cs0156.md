---
title: "Error del compilador CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0156
No se permite una instrucción throw sin argumentos en una cláusula finally anidada en la cláusula catch más cercana  
  
 Una instrucción [throw](/dotnet/csharp/language-reference/keywords/throw) sin parámetros solo puede aparecer en una cláusula **catch** que no tome parámetros.  
  
 Para más información, vea [Instrucciones para el control de excepciones](/dotnet/csharp/language-reference/keywords/exception-handling-statements) y [Excepciones y control de excepciones](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 El ejemplo siguiente genera la advertencia CS0156:  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```