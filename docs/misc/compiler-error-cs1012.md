---
title: "Error del compilador CS1012 | Microsoft Docs"
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
  - "CS1012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1012"
ms.assetid: 4acc5fe0-da47-4882-b7d8-557767d7cf03
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1012
Demasiados caracteres en literal de carácter  
  
 Se intentó inicializar una constante [char](/dotnet/csharp/language-reference/keywords/char) con más de un carácter.  
  
 El error CS1012 también puede producirse al realizar el enlace de datos. Por ejemplo, la línea siguiente generará un error:  
  
 `<%# DataBinder.Eval(Container.DataItem, 'doctitle') %>`  
  
 Pruebe la línea siguiente en su lugar:  
  
 `<%# DataBinder.Eval(Container.DataItem, "doctitle") %>`  
  
 El ejemplo siguiente genera la advertencia CS1012:  
  
```  
// CS1012.cs class Sample { static void Main() { char a = 'xx';   // CS1012 char a2 = 'x';   // OK System.Console.WriteLine(a2); } }  
```