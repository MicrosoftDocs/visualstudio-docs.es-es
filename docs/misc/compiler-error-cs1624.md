---
title: "Error del compilador CS1624 | Microsoft Docs"
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
  - "CS1624"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1624"
ms.assetid: af7d049d-27e2-4ce1-973c-5c2cb3e56a63
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1624
El cuerpo de 'accessor' no puede ser un bloque de iteradores porque 'type' no es un tipo de interfaz de iteradores.  
  
 Este error se produce si se utiliza un descriptor de acceso de iterador pero el tipo de valor devuelto no es uno de los tipos de interfaz de iterador: <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>. Para evitar este error, utilice uno de los tipos de interfaz de iterador como tipo de valor devuelto.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1624:  
  
```  
// CS1624.cs using System; using System.Collections; class C { public int Iterator // Try this instead: // public IEnumerable Iterator { get  // CS1624 { yield return 1; } } }  
```