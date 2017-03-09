---
title: "&#39;Try&#39; debe terminar con la instrucci&#243;n &#39;End Try&#39; correspondiente. | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Try&#39; debe terminar con la instrucci&#243;n &#39;End Try&#39; correspondiente.
`Try` se usa para iniciar un bloque `Try`; por lo tanto, solo puede aparecer al principio del bloque, con una instrucción`End Try` coincidente al final del bloque. Hay un instrucción `Try` redundante o no ha terminado su bloque `Try` con `Finally`.  
  
 **Identificador de error:** BC30384  
  
### Para corregir este error  
  
1.  Busque y quite las instrucciones `Try` extrañas o termine el bloque con una instrucción `End Try` coincidente.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)