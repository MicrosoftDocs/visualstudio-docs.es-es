---
title: "Error del compilador CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1651
Los campos del campo de solo lectura estático 'identifier' no se pueden pasar como out o ref \(excepto en un constructor estático\)  
  
 Este error se produce si se pasa una variable a una función que sea miembro de un campo estático de solo lectura como un argumento ref. Como la función puede modificar los parámetros red, esto no se permite. Para resolver este error, quite la palabra clave **readonly** del campo o no pase los miembros del campo readonly a la función. Por ejemplo, puede intentar crear una variable temporal que se pueda modificar y pasarla como un argumento red, como se muestra en el ejemplo siguiente.  
  
 El ejemplo siguiente genera la advertencia CS1651:  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```