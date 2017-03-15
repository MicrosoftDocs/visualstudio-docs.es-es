---
title: "Error del compilador CS0542 | Microsoft Docs"
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
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0542
'user\-defined type': los nombres de los miembros no pueden coincidir con sus tipos envolventes  
  
 Los miembros de una clase o una estructura no pueden tener el mismo nombre que la clase o la estructura, a menos que el miembro sea un constructor.  
  
 El ejemplo siguiente genera la advertencia CS0542:  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 Este error podría producirse si coloca accidentalmente un tipo de valor devuelto en un constructor, que a todos los efectos se convierte en un método normal. En el ejemplo siguiente se genera el error CS0542 porque `F` es un método, no un constructor, ya que tiene un tipo de valor devuelto:  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 Si la clase se denomina 'Item' y tiene un indizador declarado como `this`, puede que obtenga este error. Se asigna a un indizador predeterminado el nombre 'Item' en el código emitido, lo que crea el conflicto.  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```