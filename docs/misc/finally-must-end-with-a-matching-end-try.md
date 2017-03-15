---
title: "&#39;Finally&#39; debe terminar con una instrucci&#243;n &#39;End Try&#39; correspondiente | Microsoft Docs"
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
  - "vbc30442"
  - "bc30442"
helpviewer_keywords: 
  - "BC30442"
ms.assetid: 36cce657-186c-4ba0-a760-abcef9529f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; debe terminar con una instrucci&#243;n &#39;End Try&#39; correspondiente
Una instrucción `Finally` aparece en el código sin su instrucción `End Try`correspondiente. Las instrucciones `Finally` deben terminar con una instrucción `End Try`.  
  
 **Id. de error:** BC30442  
  
### Para corregir este error  
  
1.  Quite la instrucción `Finally`.  
  
2.  Agregue una instrucción `End Try` para concluir el bloque.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)