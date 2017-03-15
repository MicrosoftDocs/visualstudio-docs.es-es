---
title: "&#39;Catch&#39; no puede aparecer despu&#233;s de &#39;Finally&#39; dentro de una instrucci&#243;n &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30379"
  - "bc30379"
helpviewer_keywords: 
  - "BC30379"
ms.assetid: 33d1278b-cf10-4c66-aaf8-08a4372f370b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; no puede aparecer despu&#233;s de &#39;Finally&#39; dentro de una instrucci&#243;n &#39;Try&#39;
Una instrucción `Catch` aparece en el código después del elemento `Finally` que finaliza un bloque de instrucciones `Try`.`Catch` debe aparecer dentro de un bloque de instrucciones `Try...Catch...Finally`.  
  
 **Id. de error:** BC30379  
  
### Para corregir este error  
  
1.  Mueva la instrucción `Catch` a un lugar más adecuado del código.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)