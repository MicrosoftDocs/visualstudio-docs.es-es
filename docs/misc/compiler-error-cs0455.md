---
title: "Error del compilador CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0455
El parámetro de tipo 'Type Parameter Name' hereda las restricciones conflictivas 'Constraint Name 1' y 'Constraint Name 2'  
  
 Dos formas habituales de obtener este error son el establecimiento de restricciones para que el parámetro de tipo se derive de dos clases no relacionadas, o para que se derive de una restricción de tipo de referencia o de tipo de clase y una restricción `struct` de tipo o tipo de valor. Para solucionar este error, quite el conflicto de la jerarquía de herencia.  
  
## Ejemplo  
 El código siguiente genera el error CS0455.  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```