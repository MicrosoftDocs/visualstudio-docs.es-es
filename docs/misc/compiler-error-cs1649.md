---
title: "Error del compilador CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1649
Los miembros del campo de solo lectura 'identifier' no se pueden pasar como out o ref \(excepto en un constructor\)  
  
 Este error se produce si se pasa una variable a una función que sea miembro de un campo `readonly` como un argumento `ref` o `out`. Como la función puede modificar los parámetros `ref` y `out`, esto no está permitido. Para resolver este error, quite la palabra clave `readonly` en el campo o no pase los miembros del campo `readonly` a la función. Por ejemplo, puede intentar crear una variable temporal que se pueda modificar y pasarla como un argumento `ref`, como se muestra en el ejemplo siguiente.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1649:  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```