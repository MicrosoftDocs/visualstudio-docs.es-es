---
title: "Error del compilador CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0191
No se puede asignar la propiedad o el indexador 'nombre' \(es de solo lectura\).  
  
 Un campo [readonly](/dotnet/csharp/language-reference/keywords/readonly) solo puede tomar una asignación en un constructor o en la declaración. Para obtener más información, consulta [Constructores](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 CS0191 también se produce si el campo `readonly` es [static](/dotnet/csharp/language-reference/keywords/static) y el constructor no está marcado como `static`.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0191.  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```