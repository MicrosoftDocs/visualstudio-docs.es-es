---
title: "Error del compilador CS0631 | Microsoft Docs"
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
  - "CS0631"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0631"
ms.assetid: 5ae06b13-7874-4d0d-b256-7d8b33396156
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0631
ref y out no son válidos en este contexto  
  
 La declaración de un [indexador](/dotnet/csharp/programming-guide/indexers/index) no puede incluir el uso de los parámetros [out](/dotnet/csharp/language-reference/keywords/out) o [ref](/dotnet/csharp/language-reference/keywords/ref).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0631:  
  
```  
// CS0631.cs public class MyClass { public int this[ref int i]   // CS0631 // try the following line instead // public int this[int i] { get { return 0; } } } public class MyClass2 { public static void Main() { } }  
```