---
title: "Error del compilador CS0220 | Microsoft Docs"
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
  - "CS0220"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0220"
ms.assetid: f520bf34-bff8-4796-882b-1a9b1d5b977c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0220
La operación se desborda en el momento de la compilación en modo checked  
  
 Se detectó una operación mediante [checked](/dotnet/csharp/language-reference/keywords/checked), que es el valor predeterminado, y tuvo como resultado una pérdida de datos. Corrija las entradas de la asignación o use [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) para resolver este error. Para obtener más información, consulta [Checked y unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 El ejemplo siguiente genera la advertencia CS0220:  
  
```  
// CS0220.cs using System; class TestClass { const int x = 1000000; const int y = 1000000; public int MethodCh() { int z = (x * y);   // CS0220 return z; } public int MethodUnCh() { unchecked { int z = (x * y); return z; } } public static void Main() { TestClass myObject = new TestClass(); Console.WriteLine("Checked  : {0}", myObject.MethodCh()); Console.WriteLine("Unchecked: {0}", myObject.MethodUnCh()); } }  
```