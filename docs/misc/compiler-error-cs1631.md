---
title: "Error del compilador CS1631 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1631"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1631"
ms.assetid: bf0c5ff9-90a3-4db6-b4ee-0b93e31614e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1631
No se puede proporcionar ningún valor en el cuerpo de una cláusula catch  
  
 No se permite la instrucción yield dentro del cuerpo de una cláusula catch. Para evitar este error, mueva la instrucción yield fuera del cuerpo de la cláusula catch.  
  
 El ejemplo siguiente genera la advertencia CS1631:  
  
```  
// CS1631.cs using System; using System.Collections; public class C : IEnumerable { public IEnumerator GetEnumerator() { try { } catch(Exception e) { yield return this;  // CS1631 } } public static void Main() { } }  
```