---
title: "&#39;While&#39; debe terminar con la instrucci&#243;n &#39;End While&#39; correspondiente. | Microsoft Docs"
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
  - "bc30082"
  - "vbc30082"
helpviewer_keywords: 
  - "BC30082"
ms.assetid: 50b722b1-906f-4cb1-b5d4-fefab2ba3907
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;While&#39; debe terminar con la instrucci&#243;n &#39;End While&#39; correspondiente.
Una instrucción `While` aparece sin su instrucción `End While` correspondiente. Una instrucción `End While` debe usarse para finalizar el bloque `While`.  
  
 **Identificador de error:** BC30082  
  
### Para corregir este error  
  
1.  Si este bloque `While` forma parte de un conjunto de bloques `While` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Agregue una instrucción `End While` al final del bloque `While`.  
  
## Vea también  
 [While...End While \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)