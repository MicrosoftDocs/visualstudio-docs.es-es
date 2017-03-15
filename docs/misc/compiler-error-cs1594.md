---
title: "Error del compilador CS1594 | Microsoft Docs"
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
  - "CS1594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1594"
ms.assetid: f949a992-27a3-470d-b512-e590e5170af3
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1594
El delegado 'delegate' tiene algunos argumentos no válidos  
  
 El tipo de un argumento pasados a una invocación [delegate](/dotnet/csharp/language-reference/keywords/delegate) no concuerda con el tipo del parámetro de la declaración de delegado.  
  
 El ejemplo siguiente genera la advertencia CS1594:  
  
```  
// CS1594.cs using System; delegate string func(int i);   // declare delegate class a { public static void Main() { func dt = new func(z); x(dt); } public static string z(int j) { Console.WriteLine(j); return j.ToString(); } public static void x(func hello) { hello("8");   // CS1594 // try the following line instead // hello(8); } }  
```