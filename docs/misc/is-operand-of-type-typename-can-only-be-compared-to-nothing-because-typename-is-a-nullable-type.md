---
title: "El operando &#39;Is&#39; de tipo &#39;typename&#39; solo se puede comparar con &#39;Nothing&#39;, porque &#39;typename&#39; es un tipo que acepta valores NULL | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando &#39;Is&#39; de tipo &#39;typename&#39; solo se puede comparar con &#39;Nothing&#39;, porque &#39;typename&#39; es un tipo que acepta valores NULL
Una variable declarada como que acepta valores NULL se ha comparado con una expresión distinta de `Nothing` con el operador `Is`.  
  
 **Id. de error:** BC32127  
  
### Para corregir este error  
  
1.  Para comparar un tipo que acepta valores NULL con una expresión distinta de `Nothing` con el operador `Is`, llame al método `GetType` en el tipo que acepta valores NULL y compare el resultado con la expresión, como se muestra en el ejemplo siguiente.  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator)