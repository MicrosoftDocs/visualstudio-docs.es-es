---
title: "Advertencia del compilador (nivel 3) CS0642 | Microsoft Docs"
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
  - "CS0642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0642"
ms.assetid: e2df58c0-9b7e-4e50-8e31-e0134955f62c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 3) CS0642
Posible instrucción vacía errónea  
  
 Un punto y coma después de una instrucción condicional puede hacer que su código se ejecute de forma diferente a lo esperado.  
  
 Puede usar la opción del compilador **\/nowarn** o `#pragmas warning` para deshabilitar esta advertencia; vea [\/nowarn \(Suppress Specified Warnings\)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) o [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) para más información.  
  
 El ejemplo siguiente genera la advertencia CS0642:  
  
```  
// CS0642.cs // compile with: /W:3 class MyClass { public static void Main() { int i; for (i = 0; i < 10; i += 1);   // CS0642 semicolon intentional? { System.Console.WriteLine (i); } } }  
```