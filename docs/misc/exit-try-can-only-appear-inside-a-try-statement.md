---
title: "&#39;Exit Try&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Try&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Try&#39;
`Exit Try` solo puede aparecer dentro de una instrucción de bloque `Try`. O tiene una instrucción `Exit Try` redundante o la instrucción `Exit Try` aparece fuera de los límites del bloque `Try` correspondiente.  
  
 **Identificador de error:** BC30393  
  
### Para corregir este error  
  
1.  Busque y quite la instrucción `Exit Try` innecesaria.  
  
2.  Mueva la instrucción `Exit Try` a la ubicación adecuada del código.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)