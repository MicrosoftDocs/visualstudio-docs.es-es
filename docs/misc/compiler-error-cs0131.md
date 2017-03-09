---
title: "Error del compilador CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0131
La parte izquierda de una asignación debe ser una variable, una propiedad o un indizador  
  
 En una instrucción de asignación, el valor del lado derecho se asignó al lado izquierdo. El lado izquierdo debe ser una variable, una propiedad o un indexador.  
  
 Para corregir este error, asegúrese de que todos los operadores estén en el lado derecho y de que el lado izquierdo sea una variable, una propiedad o un indexador. Para obtener más información, consulta [Instrucciones, expresiones y operadores](/dotnet/csharp/programming-guide/statements-expressions-operators/index).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0131.  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## Ejemplo  
 Este error también puede producirse si intenta realizar operaciones aritméticas en el lado izquierdo de un operador de asignación, como en el ejemplo siguiente.  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```