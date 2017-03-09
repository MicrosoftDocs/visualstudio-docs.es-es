---
title: "Error del compilador CS1593 | Microsoft Docs"
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
  - "CS1593"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1593"
ms.assetid: 7476e799-8a8d-457d-b4e7-2d5e073799d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1593
El delegado 'del' no toma argumentos 'number'  
  
 El número de argumentos pasados a una invocación [delegate](/dotnet/csharp/language-reference/keywords/delegate) no coincide con el número de parámetros de la declaración de delegado.  
  
 El ejemplo siguiente genera la advertencia CS1593:  
  
```  
// CS1593.cs using System; delegate string func(int i);   // declare delegate class a { public static void Main() { func dt = new func(z); x(dt); } public static string z(int j) { Console.WriteLine(j); return j.ToString(); } public static void x(func hello) { hello(8, 9);   // CS1593 // try the following line instead // hello(8); } }  
```