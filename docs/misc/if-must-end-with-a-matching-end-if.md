---
title: "&#39;If&#39; debe terminar con la instrucci&#243;n &#39;End If&#39; correspondiente. | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; debe terminar con la instrucci&#243;n &#39;End If&#39; correspondiente.
Una instrucción `If` aparece sin ninguna instrucción `End If` correspondiente. Una instrucción `End If` debe usarse para finalizar el bloque `If`.  
  
 **Identificador de error:** BC30081  
  
### Para corregir este error  
  
1.  Si este bloque `If` forma parte de un conjunto de bloques `If` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Agregue una instrucción `End If` al final del bloque `If`.  
  
## Vea también  
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)