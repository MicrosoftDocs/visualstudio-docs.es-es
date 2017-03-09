---
title: "Error del compilador CS0564 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0564
El primer operando de un operador de desplazamiento sobrecargado debe tener el mismo tipo que el tipo contenedor, y el tipo del segundo operando debe ser int  
  
 Intentó sobrecargar un operador de desplazamiento \(\<\< o \>\>\) con operandos con tipos incorrectos. El primer operando debe ser el tipo y el segundo debe ser del tipo `int`.  
  
 El ejemplo siguiente genera la advertencia CS0564:  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```