---
title: "Error del compilador CS1601 | Microsoft Docs"
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
  - "CS1601"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1601"
ms.assetid: 5efa1d2d-c70c-446d-a51f-d23d8a3be22e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1601
El parámetro de método o de delegado no puede ser del tipo 'tipo'  
  
 Algunos tipos de la biblioteca de clases de .NET Framework como, por ejemplo, <xref:System.TypedReference>, <xref:System.RuntimeArgumentHandle> y <xref:System.ArgIterator>, no pueden usarse como parámetros [out](/dotnet/csharp/language-reference/keywords/out) o [ref](/dotnet/csharp/language-reference/keywords/ref) porque podrían emplearse para realizar operaciones no seguras.  
  
 El ejemplo siguiente genera la advertencia CS1601:  
  
```  
// CS1601.cs using System; class MyClass { public void Test1 (ref TypedReference t)   // CS1601 { } public void Test2 (out ArgIterator t)   // CS1601 { } }  
```