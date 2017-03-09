---
title: "Error del compilador CS0225 | Microsoft Docs"
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
  - "CS0225"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0225"
ms.assetid: 0b0cd72b-c47a-44d1-9b27-d1a1fad06807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0225
El parámetro params debe ser una matriz unidimensional  
  
 Cuando se usa la palabra clave [params](/dotnet/csharp/language-reference/keywords/params), debe especificar una matriz unidimensional del tipo de datos. Para obtener más información, consulta [Métodos](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0225:  
  
```  
// CS0225.cs public class MyClass { public static void TestParams(params int a)   // CS0225 // try the following line instead // public static void TestParams(params int[] a) { } public static void Main() { TestParams(1); } }  
```