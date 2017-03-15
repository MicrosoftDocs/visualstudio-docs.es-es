---
title: "Error del compilador CS0549 | Microsoft Docs"
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
  - "CS0549"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0549"
ms.assetid: ae965019-9dee-4f28-9e9a-6f379bd0d757
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0549
'function' es un nuevo miembro virtual en una clase sellada 'class'.  
  
 Una [clase](/dotnet/csharp/language-reference/keywords/sealed) [sellada](/dotnet/csharp/language-reference/keywords/class) no se puede utilizar como clase base.  Por lo tanto, es inútil tener un método virtual en una clase sellada.  
  
 El ejemplo siguiente genera la advertencia CS0549:  
  
```  
// CS0549.cs // compile with: /target:library sealed public class MyClass { virtual public void TestMethod() {}   // CS0549 public void TestMethod2() {}   // OK }  
```