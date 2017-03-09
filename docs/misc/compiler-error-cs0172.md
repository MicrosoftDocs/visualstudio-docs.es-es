---
title: "Error del compilador CS0172 | Microsoft Docs"
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
  - "CS0172"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0172"
ms.assetid: 1272c575-3580-4897-95fb-83f45d7435ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0172
No se puede determinar el tipo de expresión condicional porque 'type1' y 'type2' se convierten implícitamente uno en el otro  
  
 En una instrucción condicional, debe poder convertir los tipos de ambos lados del operador `:`. Además, no puede haber rutinas de conversión mutua; solo se necesita una conversión. Para obtener más información, consulta [Operadores de conversión](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 El ejemplo siguiente genera la advertencia CS0172:  
  
```  
// CS0172.cs public class Square { public class Circle { public static implicit operator Circle(Square aa) { return null; } public static implicit operator Square(Circle aa) // using explicit resolves this error // public static explicit operator Square(Circle aa) { return null; } } public static void Main() { Circle aa = new Circle(); Square ii = new Square(); object o = (1 == 1) ? aa : ii;   // CS0172 // the following cast would resolve this error // (1 == 1) ? aa : (Circle)ii; } }  
```