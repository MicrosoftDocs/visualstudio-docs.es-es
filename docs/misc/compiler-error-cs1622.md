---
title: "Error del compilador CS1622 | Microsoft Docs"
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
  - "CS1622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1622"
ms.assetid: 6b53a777-4cd8-423a-84ff-22ff588044d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1622
No se puede devolver un valor a partir de un iterador. Utilice la instrucción yield return para devolver un valor o yield break para terminar la iteración.  
  
 Un iterador es una función especial que devuelve un valor a través de la instrucción yield en lugar de la instrucción return. Para más información, vea **Iteradores**.  
  
 El ejemplo siguiente genera la advertencia CS1622:  
  
```  
// CS1622.cs // compile with: /target:library using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { return (IEnumerator) this;  // CS1622 yield return this;   // OK } }  
```