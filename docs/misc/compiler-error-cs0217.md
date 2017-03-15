---
title: "Error del compilador CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0217
Para que se pueda aplicar un operador de cortocircuito, un operador lógico definido por el usuario \('operator'\) debe tener el mismo tipo de valor devuelto que sus dos parámetros.  
  
 Si define un operador para un tipo definido por el usuario y, luego, intenta usarlo como un operador de cortocircuito, el operador definido por el usuario debe tener parámetros y valores devueltos del mismo tipo. Para obtener más información sobre los operadores de cortocircuito, vea [Operador &&](/dotnet/csharp/language-reference/operators/conditional-and-operator) y [Operador &#124;&#124;](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 El ejemplo siguiente genera la advertencia CS0217:  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## Vea también  
 [Operadores sobrecargables](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)