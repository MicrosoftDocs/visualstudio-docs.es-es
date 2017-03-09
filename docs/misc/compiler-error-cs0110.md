---
title: "Error del compilador CS0110 | Microsoft Docs"
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
  - "CS0110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0110"
ms.assetid: 0bfe7071-1194-4142-a1a1-6190ee92b1d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0110
La evaluación del valor constante para 'const declaration' comprende una definición circular  
  
 La declaración de una variable [const](/dotnet/csharp/language-reference/keywords/const) \(`a`\) no puede hacer referencia a otra variable const \(`b`\) a la que también hace referencia \(`a`\).  
  
 El ejemplo siguiente genera la advertencia CS0110:  
  
```  
// CS0110.cs namespace MyNamespace { public class A { public static void Main() { } } public class B : A { public const int i = c + 1;   // CS0110, c already references i public const int c = i + 1; // the following line would be OK // public const int c = 10; } }  
```  
  
## Vea también  
 [Constantes](/dotnet/csharp/programming-guide/classes-and-structs/constants)