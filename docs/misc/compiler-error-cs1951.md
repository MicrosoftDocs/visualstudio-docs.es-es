---
title: "Error del compilador CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1951
Una expresión lambda de árboles de expresión no puede contener un parámetro out o ref.  
  
 Un árbol de expresión representa solo expresiones como estructuras de datos. No hay ninguna manera de representar ubicaciones de memoria concretas como es necesario cuando se pasa un parámetro por referencia.  
  
### Para corregir este error  
  
1.  La única opción es quitar el modificador `ref` en la definición de delegado y pasar el parámetro por valor.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1951:  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## Vea también  
 [Árboles de expresión](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)