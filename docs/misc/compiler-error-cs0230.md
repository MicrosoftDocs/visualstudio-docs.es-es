---
title: "Error del compilador CS0230 | Microsoft Docs"
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
  - "CS0230"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0230"
ms.assetid: 132e4623-d393-4a5f-a3f8-838a1bfbd1b3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0230
En una instrucción foreach se requieren un tipo y un identificador  
  
 Una instrucción [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) está mal formada.  
  
 El ejemplo siguiente genera la advertencia CS0230:  
  
```  
// CS0230.cs using System; class MyClass { public static void Main() { int[] myarray = new int[3] {1,2,3}; foreach (int in myarray)   // CS0230 // try the following line instead // foreach (int x in myarray) { Console.WriteLine(x); } } }  
```