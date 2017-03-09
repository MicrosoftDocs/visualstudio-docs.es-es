---
title: "Error del compilador CS0213 | Microsoft Docs"
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
  - "CS0213"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0213"
ms.assetid: 3c1d55e3-2b84-4c28-8206-ef65869a898c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0213
No se puede usar la instrucción fixed para adquirir la dirección de una expresión de tipo fixed  
  
 Una variable local en un parámetro o en un método [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) ya está fija \(en la pila\), por lo que no puede tomar la dirección de ninguna de estas dos variables en una expresión [fija](/dotnet/csharp/language-reference/keywords/fixed-statement). Para obtener más información, consulta [Código no seguro y punteros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0213.  
  
```  
// CS0213.cs // compile with: /unsafe public class MyClass { unsafe public static void Main() { int i = 45; fixed (int *j = &i) { }  // CS0213 // try the following line instead // int* j = &i; int[] a = new int[] {1,2,3}; fixed (int *b = a) { fixed (int *c = b) { }  // CS0213 // try the following line instead // int *c = b; } } }  
```