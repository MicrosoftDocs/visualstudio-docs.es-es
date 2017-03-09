---
title: "&#39;Else&#39; debe ir precedida de la instrucci&#243;n &#39;If&#39; o &#39;ElseIf&#39; correspondiente | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Else&#39; debe ir precedida de la instrucci&#243;n &#39;If&#39; o &#39;ElseIf&#39; correspondiente
Una instrucción `Else` aparece sin una instrucción `If` correspondiente. La instrucción `Else` debe ir precedida de una instrucción `If`.  
  
 **Identificador de error:** BC30086  
  
### Para corregir este error  
  
1.  Si este bloque `If` forma parte de un conjunto de bloques `If` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Compruebe que el resto de las estructuras de control dentro del bloque `If` estén terminadas correctamente.  
  
3.  Asegúrese de que este bloque `If` tenga el formato correcto.  
  
## Vea también  
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)