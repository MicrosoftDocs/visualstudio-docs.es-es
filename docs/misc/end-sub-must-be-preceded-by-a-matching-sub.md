---
title: "&#39;End Sub&#39; debe ir precedida de la instrucci&#243;n &#39;Sub&#39; correspondiente | Microsoft Docs"
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
  - "vbc30429"
  - "bc30429"
helpviewer_keywords: 
  - "BC30429"
ms.assetid: cf9d0cfe-5dfa-4f6d-9d10-69eb16e413e1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Sub&#39; debe ir precedida de la instrucci&#243;n &#39;Sub&#39; correspondiente
Una instrucción `End Sub` aparece en el código sin ninguna definición de procedimiento `Sub` coincidente que la preceda.  
  
 **Id. de error:** BC30429  
  
### Para corregir este error  
  
-   Quite la instrucción `End Sub` si es redundante.  
  
-   Facilite el procedimiento `Sub` si falta alguno.  
  
-   Mueva la instrucción `End Sub` al lugar adecuado del código.  
  
## Vea también  
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [End \<palabra clave\> \(Instrucción\)](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)