---
title: "Error del compilador CS0459 | Microsoft Docs"
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
  - "CS0459"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0459"
ms.assetid: 01b058dd-8d65-4e9d-9de1-d47f9488d22a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0459
No se puede adquirir la dirección de una variable local de solo lectura  
  
 Hay tres escenarios comunes en el lenguaje C\# que generan variables locales de solo lectura: `foreach`, `using` y `fixed`. En cada uno de estos casos, no se permite escribir en la variable local de solo lectura ni tomar su dirección. Este error se genera cuando el compilador detecta que se está intentando tomar la dirección de una variable local de solo lectura.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0459 cuando se intenta tomar la dirección de una variable local de solo lectura en un bucle `foreach` y en un bloque de instrucciones `fixed`.  
  
```  
// CS0459.cs // compile with: /unsafe class A { public unsafe void M1() { int[] ints = new int[] { 1, 2, 3 }; foreach (int i in ints) { int *j = &i;  // CS0459 } fixed (int *i = &_i) { int **j = &i;  // CS0459 } } private int _i = 0; }  
```