---
title: "Error del compilador CS1101 | Microsoft Docs"
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
  - "CS1101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1101"
ms.assetid: d6fc8834-eadf-4497-b442-0751895e6764
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1101
El modificador de parámetro 'ref' no se puede usar con 'this'  
  
 Cuando la palabra clave `this` modifica el primer parámetro de un método estático, indica al compilador que el método es un método de extensión. No se necesiten ni se permiten otros modificadores en el primer parámetro de un método de extensión.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1101:  
  
```  
// cs1101.cs // Compile with: /target:library public static class Extensions { // No type parameters. public static void Test(ref this int i) {} // CS1101 // Single type parameter. public static void Test<T>(ref this T t) {}// CS1101 // Multiple type parameters. public static void Test<T,U,V>(ref this U u) {}// CS1101 }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [ref](/dotnet/csharp/language-reference/keywords/ref)