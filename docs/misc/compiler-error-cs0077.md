---
title: "Error del compilador CS0077 | Microsoft Docs"
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
  - "CS0077"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0077"
ms.assetid: 55d3d290-d172-41a3-b326-ebf5a0a7e81f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0077
El operador as se debe usar con un tipo de referencia o un tipo que acepta valores NULL \('int' es un tipo de valor que no acepta valores NULL\)  
  
 Se pasó al operador [as](/dotnet/csharp/language-reference/keywords/as) un [tipo de valor](/dotnet/csharp/language-reference/keywords/value-types). Puesto que `as` puede devolver [null](/dotnet/csharp/language-reference/keywords/null), solo se le pueden pasar [tipos de referencia](/dotnet/csharp/language-reference/keywords/reference-types) o un tipo que acepta valores NULL. Para obtener más información sobre los tipos que aceptan valores NULL, vea [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index).  
  
 El ejemplo siguiente genera la advertencia CS0077:  
  
```  
// CS0077.cs using System; class C { } struct S { } class M { public static void Main() { object o1, o2; C c; S s; o1 = new C(); o2 = new S(); s = o2 as S;  // CS0077, S is not a reference type. // try the following line instead // c = o1 as C; } }  
```