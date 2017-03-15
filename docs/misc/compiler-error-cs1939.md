---
title: "Error del compilador CS1939 | Microsoft Docs"
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
  - "CS1939"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1939"
ms.assetid: 9a7cdd48-3d45-473a-a799-c7771ef8158d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1939
No se puede pasar la variable de rango 'nombre' como parámetro out o ref.  
  
 Una variable de rango es una variable de solo lectura que se incluye en una expresión de consulta y actúa como un identificador para cada elemento sucesivo de una secuencia de origen. Dado que no puede modificarse de ninguna manera, no existe razón para pasarla por `ref` o `out`. Por lo tanto, ambas operaciones no son válidas.  
  
### Para corregir este error  
  
1.  Pase la variable de rango por valor.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1939:  
  
```  
// cs1939.cs using System.Linq; class Test { public static void F(ref int i) { } public static void Main() { var list = new int[] { 0, 1, 2, 3, 4, 5 }; var q = from x in list let k = x select Test.F(ref x); // CS1939 } }  
```