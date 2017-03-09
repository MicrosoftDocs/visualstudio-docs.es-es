---
title: "Error del compilador CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0199
Los campos del campo de solo lectura estático 'name' no se pueden pasar como out ni ref \(excepto en un constructor estático\)  
  
 Una variable [readonly](/dotnet/csharp/language-reference/keywords/readonly) debe tener el mismo uso de [static](/dotnet/csharp/language-reference/keywords/static) que el constructor en el que quiere pasarla como un parámetro [ref](/dotnet/csharp/language-reference/keywords/ref) o [out](/dotnet/csharp/language-reference/keywords/out). Para obtener más información, consulta [Pasar parámetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0199:  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```