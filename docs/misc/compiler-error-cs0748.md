---
title: "Error del compilador CS0748 | Microsoft Docs"
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
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0748
Uso incoherente del parámetro lambda; todos los tipos de parámetro deben ser explícitos o implícitos.  
  
 Si una expresión lambda tiene varios parámetros de entrada, algunos parámetros no pueden usar tipos implícitos mientras que otros usan tipos explícitos.  
  
### Para corregir este error  
  
1.  Proporcione a todos los parámetros de entrada tipos implícitos, o bien proporcione tipos explícitos.  
  
## Ejemplo  
 El código siguiente genera el error CS0748 porque, en la expresión lambda, solo `alpha` tiene un tipo explícito:  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## Vea también  
 [Expresiones lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)