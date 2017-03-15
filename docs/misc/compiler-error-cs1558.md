---
title: "Error del compilador CS1558 | Microsoft Docs"
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
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1558
'clase' no tiene ningún método Main estático adecuado  
  
 La opción del compilador [\/main](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) especificó una clase en la que buscar un método **Main**. Sin embargo, el método [Main](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) no se definió correctamente.  
  
 En el siguiente ejemplo se genera el error CS1558 debido a un tipo de valor devuelto no válido.  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```