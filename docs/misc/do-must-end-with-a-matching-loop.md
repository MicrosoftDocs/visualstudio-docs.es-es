---
title: "&#39;Do&#39; debe terminar con la instrucci&#243;n &#39;Loop&#39; correspondiente. | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Do&#39; debe terminar con la instrucci&#243;n &#39;Loop&#39; correspondiente.
Una instrucción `Do` aparece sin su instrucción `Loop` correspondiente. Una instrucción `Loop` debe usarse para finalizar el bucle `Do`.  
  
 **Identificador de error:** BC30083  
  
### Para corregir este error  
  
-   Si este bucle `Do` forma parte de un conjunto de bucles anidados, asegúrese de que cada bucle finaliza correctamente.  
  
-   Agregue una instrucción `Loop` al final del bucle `Do`.  
  
## Vea también  
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)