---
title: "&#39;Catch&#39; debe terminar con la instrucci&#243;n &#39;End Try&#39; correspondiente. | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; debe terminar con la instrucci&#243;n &#39;End Try&#39; correspondiente.
Una instrucción `Catch` aparece en el código sin su instrucción `End Try` correspondiente. Las instrucciones `Catch` deben terminar con una instrucción `End Try`.  
  
 **Id. de error:** BC30441  
  
### Para corregir este error  
  
1.  Quite la instrucción `Catch`.  
  
2.  Agregue una instrucción `End Try` para concluir el bloque.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)