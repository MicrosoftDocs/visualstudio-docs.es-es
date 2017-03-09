---
title: "Error del compilador CS0177 | Microsoft Docs"
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
  - "CS0177"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0177"
ms.assetid: 852a8c2a-2411-4800-af7c-4c572d9900d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0177
Es necesario asignar el parámetro out 'parameter' antes de que el control abandone el método actual  
  
 Un parámetro marcado con la palabra clave [out](/dotnet/csharp/language-reference/keywords/out) no tenía un valor asignado en el cuerpo del método. Para obtener más información, vea [Pasar parámetros](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)  
  
 El ejemplo siguiente genera la advertencia CS0177:  
  
```  
// CS0177.cs public class MyClass { public static void Foo(out int i)   // CS0177 { // uncomment the following line to resolve this error //   i = 0; } public static void Main() { int x = -1; Foo(out x); } }  
```