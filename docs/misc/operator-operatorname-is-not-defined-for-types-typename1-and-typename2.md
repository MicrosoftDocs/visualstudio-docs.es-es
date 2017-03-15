---
title: "El operador &#39;&lt;operatorname&gt;&#39; no est&#225; definido para los tipos &#39;&lt;typename1&gt;&#39; y &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operatorname&gt;&#39; no est&#225; definido para los tipos &#39;&lt;typename1&gt;&#39; y &#39;&lt;typename2&gt;&#39;
El operador '\<operatorname\>' no está definido para los tipos '\<typename1\>' y '\<typename2\>'. Use el operador 'Is' para comparar dos tipos de referencia.  
  
 Se ha intentado usar un operador de una manera que no es apropiada para los tipos especificados. Este error puede deberse al uso del operador "\=" en lugar del operador `Is` para comparar dos objetos.  
  
 **Id. de error:** BC31080  
  
### Para corregir este error  
  
1.  Use el operador `Is` para comparar dos tipos de referencia.  
  
2.  Use el operador `Not` junto con el operador `Is` para denotar desigualdad. Por ejemplo:  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## Vea también  
 [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [\= \(Operador\)](/dotnet/visual-basic/language-reference/operators/assignment-operator)   
 [Not \(Operador\)](/dotnet/visual-basic/language-reference/operators/not-operator)