---
title: "Error del compilador CS0306 | Microsoft Docs"
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
  - "CS0306"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0306"
ms.assetid: f340a3ce-6140-4001-bb00-628a2985ddd6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0306
El tipo 'type' no se puede usar como un argumento de tipo  
  
 No se permite el tipo usado como un parámetro de tipo. Esto podría deberse a que el tipo es un tipo de puntero.  
  
 El siguiente ejemplo genera el error CS0306:  
  
```  
// CS0306.cs class C<T> { } class M { // CS0306 – int* not allowed as a type parameter C<int*> f; }  
```