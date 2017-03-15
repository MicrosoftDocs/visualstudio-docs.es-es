---
title: "&#39;End If&#39; debe ir precedida de la instrucci&#243;n &#39;If&#39; correspondiente | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End If&#39; debe ir precedida de la instrucci&#243;n &#39;If&#39; correspondiente
Una instrucción `End If` aparece sin una instrucción `If` correspondiente. La instrucción `End If` debe ir precedida de una instrucción `If`.  
  
 **Identificador de error:** BC30087  
  
### Para corregir este error  
  
1.  Si este bloque `If` forma parte de un conjunto de bloques `If` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Compruebe que el resto de estructuras de control dentro del bloque `If` están terminadas correctamente.  
  
3.  Asegúrese de que este bloque `If` tenga el formato correcto.  
  
## Vea también  
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)