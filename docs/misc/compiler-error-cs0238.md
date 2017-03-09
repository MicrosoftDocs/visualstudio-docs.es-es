---
title: "Error del compilador CS0238 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0238"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0238"
ms.assetid: 9b50c6e2-2c3f-431d-bdb7-557b0ec51626
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0238
'miembro' no puede estar sellado porque no es una invalidación  
  
 Se usó [sealed](/dotnet/csharp/language-reference/keywords/sealed) en un miembro que tampoco estaba marcado con [override](/dotnet/csharp/language-reference/keywords/override). Para obtener más información, consulte [Herencia](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
 El ejemplo siguiente genera la advertencia CS0238:  
  
```  
// CS0238.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public sealed void f() // CS0238 // Try the following definition instead: // public override sealed void f() { } }  
```