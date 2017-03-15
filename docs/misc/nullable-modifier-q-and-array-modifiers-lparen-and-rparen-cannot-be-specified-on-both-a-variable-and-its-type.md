---
title: "El modificador &#39;?&#39; que acepta valores NULL y los modificadores de matriz &#39;(&#39; y &#39;)&#39; no se pueden especificar en una variable y su tipo a la vez. | Microsoft Docs"
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
  - "vbc33102"
  - "bc33102"
helpviewer_keywords: 
  - "BC33102"
ms.assetid: fd3f65a4-63f9-41dc-ba15-98d86f097ba8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El modificador &#39;?&#39; que acepta valores NULL y los modificadores de matriz &#39;(&#39; y &#39;)&#39; no se pueden especificar en una variable y su tipo a la vez.
Se incluye el modificador de tipo que acepta valores NULL \(?\) en la variable en una declaración de variable en la que los modificadores de matriz \(paréntesis\) se incluyen en el tipo de variable especificado. O bien, se incluye el modificador de tipo que acepta valores NULL en el tipo de variable especificado en una declaración de variable en la que los modificadores de matriz se incluyen en la variable.  
  
 **Identificador de error:** BC33102  
  
### Para corregir este error  
  
1.  Especifique el modificador de tipo que acepta valores NULL \(?\) y los modificadores de matriz \(paréntesis\) en la variable declarada o el tipo de variable especificada, tal como se muestra en el ejemplo siguiente.  
  
    ```vb#  
    ' These are incorrect. ' Dim numbers? As Integer() ' Dim values() As Integer? 'These are correct. Dim numbers?() As Integer Dim values As Integer?()  
    ```  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)