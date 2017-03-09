---
title: "Advertencia del compilador (nivel 2) CS0279 | Microsoft Docs"
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
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0279
'nombre de tipo' no implementa el patrón 'nombre de patrón'. 'nombre de método' es estático o no público.  
  
 Hay varias instrucciones en C\# que se basan en patrones definidos, como `foreach` y `using`. Por ejemplo, `foreach` se basa en la clase de colección que implementa el patrón enumerable. Este error se genera cuando el compilador no puede establecer la correspondencia porque se ha declarado un método como `static` o no `public`. Los métodos de los patrones tienen que ser obligatoriamente instancias de clases y públicos.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0279:  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```