---
title: "Error del compilador CS1626 | Microsoft Docs"
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
  - "CS1626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1626"
ms.assetid: 3ba03383-eb24-4fd8-bf40-8b0f7d6baf0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1626
No se puede proporcionar un valor en el cuerpo de un bloque try con una cláusula catch  
  
 Una instrucción yield no se permite en un bloque try si hay una cláusula catch asociada al bloque try. Para evitar este error, mueva la instrucción yield fuera de la cláusula catch.  
  
 El ejemplo siguiente genera la advertencia CS1626:  
  
```  
// CS1626.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { yield return this;  // CS1626 } catch { } } } public class CMain { public static void Main() { } }  
  
```