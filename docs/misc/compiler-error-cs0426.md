---
title: "Error del compilador CS0426 | Microsoft Docs"
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
  - "CS0426"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0426"
ms.assetid: 62df0deb-3624-436e-9691-ebe3ee1fc31f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0426
El nombre de tipo 'identificador' no existe en el tipo 'tipo'  
  
 Este error se genera cuando se hace referencia a un tipo anidado dentro de otro tipo, pero dicho tipo anidado no existe. Esto puede ocurrir si se escribe incorrectamente el nombre del tipo anidado. Compruebe la ortografía de los nombres usados y compruebe que el tipo envolvente tenga el miembro esperado.  
  
 El ejemplo siguiente genera la advertencia CS0426, porque la clase C no tiene ningún tipo anidado A:  
  
```  
// CS0426.cs class C { // No nested types are declared. } class D { public static void Main() { C c = new C(); // Attempt to reference a nested type A: C.A a; // CS0426 because no such type C.A } }  
```  
  
## Vea también  
 [Clases y structs](/dotnet/csharp/programming-guide/classes-and-structs/index)