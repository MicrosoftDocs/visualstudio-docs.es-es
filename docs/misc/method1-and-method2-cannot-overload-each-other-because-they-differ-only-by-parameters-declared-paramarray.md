---
title: "Los m&#233;todos &#39;&lt;m&#233;todo1&gt;&#39; y &#39;&lt;m&#233;todo2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en los par&#225;metros declarados &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos &#39;&lt;m&#233;todo1&gt;&#39; y &#39;&lt;m&#233;todo2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en los par&#225;metros declarados &#39;ParamArray&#39;
Ha intentado sobrecargar dos métodos que solo se diferencian entre sí en uno o varios parámetros `ParamArray`. El compilador considera que un procedimiento con un parámetro `ParamArray` tiene un número infinito de sobrecargas que se diferencian entre sí por lo que se pasa a la matriz de parámetros.  
  
 **Identificador de error:** BC30368  
  
### Para corregir este error  
  
-   Asegúrese de que los métodos se diferencian por algo más que los parámetros `ParamArray`.  
  
## Vea también  
 [Consideraciones sobre la sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Matrices de parámetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)