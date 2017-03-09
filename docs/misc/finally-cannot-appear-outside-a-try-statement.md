---
title: "&#39;Finally&#39; no puede aparecer fuera de una instrucci&#243;n &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; no puede aparecer fuera de una instrucci&#243;n &#39;Try&#39;
`Finally` se usa para completar un bloque `Try...Catch...Finally`; por lo tanto, solo puede aparecer una vez al final del bloque. O bien hay un elemento `Finally` innecesario, o la instrucción `Finally` aparece fuera de los límites de su bloque `Try` correspondiente.  
  
 **Id. de error:** BC30382  
  
### Para corregir este error  
  
1.  Busque y quite la instrucción `Finally`innecesaria.  
  
2.  Mueva la instrucción `Finally` a la ubicación adecuada del código.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general del control estructurado de excepciones en Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)