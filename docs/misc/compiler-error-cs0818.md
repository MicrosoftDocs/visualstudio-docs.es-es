---
title: "Error del compilador CS0818 | Microsoft Docs"
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
  - "CS0818"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0818"
ms.assetid: e4941018-a10a-4636-98ea-aade29e45728
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0818
Las variables locales con tipo implícito se deben inicializar.  
  
 Una variable local con tipo implícito se debe inicializar con un valor al mismo tiempo que se declara.  
  
### Para corregir este error  
  
1.  Asigne un valor a la variable o proporciónele un tipo explícito.  
  
## Ejemplo  
 El código siguiente genera el error CS0818:  
  
```  
// cs0818.cs class A { public static int Main() { var a; // CS0818 return -1; } }  
```  
  
## Vea también  
 [Variables locales con asignación implícita de tipos](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)