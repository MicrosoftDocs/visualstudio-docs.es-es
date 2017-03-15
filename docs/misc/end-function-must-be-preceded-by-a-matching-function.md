---
title: "&#39;End Function&#39; debe ir precedida de la instrucci&#243;n &#39;Function&#39; correspondiente. | Microsoft Docs"
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
  - "bc30430"
  - "vbc30430"
helpviewer_keywords: 
  - "BC30430"
ms.assetid: de66a6b4-0321-45c2-aca0-87d2b4244b31
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Function&#39; debe ir precedida de la instrucci&#243;n &#39;Function&#39; correspondiente.
Una instrucción `End Function` aparece en el código sin ninguna definición de procedimiento `Function` coincidente que la preceda.  
  
 **Identificador de error:** BC30430  
  
### Para corregir este error  
  
1.  Quite la instrucción `End Function` si es redundante.  
  
2.  Facilite el procedimiento `Function` si falta alguno.  
  
3.  Mueva la instrucción `End Function` al lugar adecuado del código.  
  
## Vea también  
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [End \<palabra clave\> \(Instrucción\)](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)