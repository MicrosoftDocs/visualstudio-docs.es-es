---
title: "Option Strict On no permite operandos de tipo Object para el operador &#39;&lt;operatorname&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite operandos de tipo Object para el operador &#39;&lt;operatorname&gt;&#39;
Option Strict On no permite operandos de tipo Object para el operador '\<operatorname\>'. Utilice el operador Is para comprobar la identidad del objeto.  
  
 Un operador de comparación aritmética como `=` se utiliza con una o varias variables de objeto cuando `Option Strict` es `On`.  
  
 **Id. de error:** BC32013  
  
### Para corregir este error  
  
1.  Establezca `Option Strict Off` si las variables de objeto contienen valores numéricos y quiere realizar una comparación aritmética.  
  
2.  Utilice el operador `Is` para comparar la identidad del objeto.  
  
## Vea también  
 [Operadores de comparación](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)