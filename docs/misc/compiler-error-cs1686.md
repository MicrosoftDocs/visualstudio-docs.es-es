---
title: "Error del compilador CS1686 | Microsoft Docs"
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
  - "CS1686"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1686"
ms.assetid: 46a9e82b-57f4-416d-8e49-242bfff5433a
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1686
No puede tomarse la dirección de la variable local 'variable' o sus miembros y usarse en un método anónimo o una expresión lambda.  
  
 Este error se genera cuando se usa una variable, se intenta tomar su dirección y se realiza una de estas acciones dentro de un método anónimo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1686.  
  
```  
// CS1686.cs // compile with: /unsafe /target:library class MyClass { public unsafe delegate int * MyDelegate(); public unsafe int * Test() { int j = 0; MyDelegate d = delegate { return &j; };   // CS1686 return &j;   // OK } }  
```