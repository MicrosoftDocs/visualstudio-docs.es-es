---
title: "Error del compilador CS0832 | Microsoft Docs"
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
  - "CS0832"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0832"
ms.assetid: b5527209-a9bd-4f8c-a432-2e89bb1905d1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0832
Un árbol de expresión no puede contener un operador de asignación.  
  
 Un árbol de expresión no conserva el estado de la variable ni tiene ningún concepto de una ubicación de almacenamiento.  
  
### Para corregir este error  
  
1.  Quite el operador de asignación de la expresión lambda o de consulta.  
  
## Ejemplo  
 En el código de ejemplo, como en todas las expresiones lambda, `x` es simplemente un parámetro de entrada que se pasa por valor. No se puede cambiar su valor en un árbol de expresión. Se puede cambiar en una lambda de delegado.  
  
```  
// cs0843.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<Func<int, int>> e = x => x += 5; // CS0843 return 1; } }  
```