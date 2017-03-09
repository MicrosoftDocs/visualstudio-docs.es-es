---
title: "Error del compilador CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1666
No puede usar los búferes de tamaño fijo contenidos en expresiones de tipo unfixed. Pruebe a usar la instrucción fixed.  
  
 Este error se produce si usa el búfer de tamaño fijo en una expresión que contiene una clase que no es de tipo fixed. El tiempo de ejecución es libre de mover la clase unfixed para optimizar el acceso a la memoria, lo que puede provocar errores al usar el búfer de tamaño fijo. Para evitar este error, use la palabra clave `fixed` en la instrucción.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1666:  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```