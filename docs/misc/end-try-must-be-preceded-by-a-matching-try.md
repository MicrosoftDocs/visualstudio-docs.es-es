---
title: "&#39;End Try&#39; debe ir precedida de la instrucci&#243;n &#39;Try&#39; correspondiente | Microsoft Docs"
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
  - "bc30383"
  - "vbc30383"
helpviewer_keywords: 
  - "BC30383"
ms.assetid: 1d13357a-ab44-4082-b204-6e2e94f4774e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Try&#39; debe ir precedida de la instrucci&#243;n &#39;Try&#39; correspondiente
`End`  `Try` se usa para completar un bloque `Try`; por lo tanto, solo puede aparecer una vez al final del bloque. O bien tiene una instrucción `End Try` redundante o su instrucción `End``Try` aparece fuera de los límites del bloque `Try` correspondiente.  
  
 **Identificador de error:** BC30383  
  
### Para corregir este error  
  
1.  Busque y quite la instrucción `End Try` innecesaria.  
  
2.  Agregue `End Try` a la ubicación adecuada en el código.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general sobre el control estructurado de excepciones de Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)