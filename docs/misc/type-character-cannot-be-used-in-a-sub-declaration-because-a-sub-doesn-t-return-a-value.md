---
title: "El car&#225;cter de tipo no se puede usar en una declaraci&#243;n &#39;Sub&#39; porque &#39;Sub&#39; no devuelve un valor | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El car&#225;cter de tipo no se puede usar en una declaraci&#243;n &#39;Sub&#39; porque &#39;Sub&#39; no devuelve un valor
Un procedimiento `Sub`, del mismo modo que un procedimiento `Function`, es un procedimiento independiente que puede tomar argumentos y realizar una serie de instrucciones. A diferencia de un procedimiento `Function`, un procedimiento `Sub` no devuelve un valor y, por tanto, no puede contener una declaración de tipo.  
  
 **Identificador de error:** BC30303  
  
### Para corregir este error  
  
-   Cambie el procedimiento `Sub` a un procedimiento `Function`.  
  
## Vea también  
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)