---
title: "Error del compilador CS1623 | Microsoft Docs"
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
  - "CS1623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1623"
ms.assetid: e52bc2d6-5116-40a2-90bc-23a3fa2c73e7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1623
Los iteradores no pueden tener parámetros ref ni out  
  
 Este error se produce si un método iterador toma un parámetro `ref` o `out`. Para evitar este error, elimine la palabra clave `ref` o `out` de la signatura del método.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1623:  
  
```  
// CS1623.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { yield return 0; } // To resolve the error, remove ref public IEnumerator GetEnumerator(ref int i)  // CS1623 { yield return i; } // To resolve the error, remove out public IEnumerator GetEnumerator(out float f)  // CS1623 { f = 0.0F; yield return f; } }  
```