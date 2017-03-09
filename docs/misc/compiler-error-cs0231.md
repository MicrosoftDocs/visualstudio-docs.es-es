---
title: "Error del compilador CS0231 | Microsoft Docs"
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
  - "CS0231"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0231"
ms.assetid: e5e6a8e1-6c9f-4a88-8935-7bedfba88f8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0231
Un parámetro params debe ser el último parámetro de una lista de parámetros formales.  
  
 El parámetro [params](/dotnet/csharp/language-reference/keywords/params) admite un número variable de argumentos y debe ser posterior a todos los demás parámetros. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 El ejemplo siguiente genera la advertencia CS0231:  
  
```  
// CS0231.cs class Test { public void TestMethod(params int[] p, int i) {} // CS0231 // To resolve the error, use the following line instead: // public void TestMethod(int i, params int[] p) {} static void Main() { } }  
```