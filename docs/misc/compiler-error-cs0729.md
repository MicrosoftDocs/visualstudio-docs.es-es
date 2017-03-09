---
title: "Error del compilador CS0729 | Microsoft Docs"
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
  - "CS0729"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0729"
ms.assetid: e0421d06-e818-404f-af97-d101272f4d07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0729
El tipo 'type' está definido en este ensamblado, pero se ha especificado un reenviador de tipos para él  
  
 No puede usar un reenviador de tipos para un tipo definido en el mismo ensamblado.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0729:  
  
```  
// CS0729.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:TypeForwardedTo(typeof(TestClass))]   // CS0729 class TestClass {}  
```