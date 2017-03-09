---
title: "&#39;Catch&#39; no puede aparecer fuera de una instrucci&#243;n &#39;Try&#39;. | Microsoft Docs"
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
  - "bc30380"
  - "vbc30380"
helpviewer_keywords: 
  - "BC30380"
ms.assetid: 73ce950d-881f-4532-8024-40a4930abd32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; no puede aparecer fuera de una instrucci&#243;n &#39;Try&#39;.
`Catch` debe aparecer dentro de un bloque de instrucciones `Try...Catch...Finally`. O bien hay una instrucción `Catch` innecesaria en su bloque `Try`, o la instrucción `Catch` aparece fuera de los límites de su bloque `Try` correspondiente.  
  
 **Identificador de error:** BC30380  
  
### Para corregir este error  
  
1.  Elimine la instrucción `Catch` si es innecesaria, o colóquela en un bloque de instrucciones `Try...Catch...Finally`.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)