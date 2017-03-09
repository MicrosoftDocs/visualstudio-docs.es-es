---
title: "Error del compilador CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0837
El primer operando de un operador "is" o "as" no puede ser una expresión lambda ni un método anónimo.  
  
 Los métodos anónimos y las expresiones lambda no pueden usarse en el lado izquierdo de [is](/dotnet/csharp/language-reference/keywords/is) o [as](/dotnet/csharp/language-reference/keywords/as).  
  
### Para corregir este error  
  
-   Si el error está relacionado con el operador `is`, recuerde que `is` toma un valor y un tipo y le indica si se puede convertir el valor en ese tipo mediante una conversión boxing, unboxing o de referencia. Como las expresiones lambda no son valores y no tienen conversiones boxing, unboxing o de referencia, las expresiones lambda no son candidatas para `is`.  
  
-   Si el código hace un uso inadecuado de `as`, probablemente la corrección lo cambiará a una conversión.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0837:  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```