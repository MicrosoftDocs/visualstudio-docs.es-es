---
title: "Error del compilador CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0182
Un argumento de atributo debe ser una expresión constante, una expresión typeof o una expresión de creación de matrices de un tipo de parámetro de atributo  
  
 Ciertas restricciones se aplican a los tipos de argumentos que se pueden usar con atributos. Tenga en cuenta que, además de las restricciones especificadas en el mensaje de error, los siguientes tipos NO pueden usarse como argumentos de atributo:  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 Para más información, vea [NO ESTÁ EN LA COMPILACIÓN: Atributos globales \(Guía de programación de C\#\)](http://msdn.microsoft.com/es-es/7c6c41f8-f0d5-4345-8987-3d91f9bae136).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0182:  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```