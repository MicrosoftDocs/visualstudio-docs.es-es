---
title: "Error del compilador CS1929 | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1929
Argumento de instancia: no se puede convertir de 'typeA' a 'typeB'.  
  
 Este error se genera cuando se intenta invocar un método de extensión de una clase que no se extiende. En este ejemplo, se define el método de extensión de la clase derivada `A`, pero no de la clase base `B`.  
  
### Para corregir este error  
  
1.  Cree un nuevo método de extensión para el tipo donde tiene que invocarlo, o bien mueva la llamada a un objeto del tipo que el método existente extiende.  
  
## Ejemplo  
 El código siguiente genera los errores CS1928 y CS1929:  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## Vea también  
 [Métodos de extensión](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)