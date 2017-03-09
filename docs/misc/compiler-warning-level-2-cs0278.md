---
title: "Advertencia del compilador (nivel 2) CS0278 | Microsoft Docs"
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
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS0278
'tipo' no implementa el patrón 'nombre de patrón'. 'nombre de método' es ambiguo con 'nombre de método'.  
  
 Hay varias instrucciones en C\# que se basan en patrones definidos, como `foreach` y `using`. Por ejemplo, `foreach` se basa en la clase de colección que implementa el patrón "enumerable".  
  
 Puede producirse la advertencia CS0278 si el compilador no puede establecer la coincidencia debido a ambigüedades. Por ejemplo, el patrón "enumerable" necesita un método llamado `MoveNext`, y el código puede contener dos métodos denominados `MoveNext`. El compilador intentará encontrar una interfaz que pueda usar, pero se recomienda que determine y resuelva la causa de la ambigüedad.  
  
 Para obtener más información, consulta [Cómo: Obtener acceso a una clase de colección mediante Foreach](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0278.  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```