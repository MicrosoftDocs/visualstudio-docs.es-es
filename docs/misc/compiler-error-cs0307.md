---
title: "Error del compilador CS0307 | Microsoft Docs"
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
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0307
El método 'construct' 'identifier' no es genérico. Si tenía prevista una lista de expresiones, use el paréntesis \< alrededor de la expresión.  
  
 La construcción denominada no era un tipo ni un método, las únicas construcciones que admiten argumentos genéricos. Quite los argumentos de tipo entre corchetes angulares. Si se necesita un tipo genérico, declare la construcción genérica como un tipo o método genérico.  
  
 El ejemplo siguiente genera la advertencia CS0307:  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```