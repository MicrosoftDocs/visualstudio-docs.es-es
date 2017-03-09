---
title: "Error del compilador CS0706 | Microsoft Docs"
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
  - "CS0706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0706"
ms.assetid: bc3ac5c0-8c96-43c8-b10a-69bd31b38e4a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0706
Tipo de restricción no válido. Un tipo usado como una restricción debe ser una interfaz, una clase no sellada o un parámetro de tipo.  
  
 Este error se produce cuando se usa una construcción no válida en una cláusula de restricción. Para evitar este error, use una interfaz o clase no sellada en lugar de la construcción que causó el error.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0706.  
  
```  
// CS0706.cs // compile with: /target:library class A {} class C<T> where T : int[] {}  // CS0706 class D<T> where T : A {}  // OK  
```