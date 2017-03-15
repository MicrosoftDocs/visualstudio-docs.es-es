---
title: "&#39;Finally&#39; solo puede aparecer una vez en una instrucci&#243;n &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30381"
  - "bc30381"
helpviewer_keywords: 
  - "BC30381"
ms.assetid: 4fa1d5fa-c54a-4f8c-9d66-9dbcc38c53bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; solo puede aparecer una vez en una instrucci&#243;n &#39;Try&#39;
`Finally` se usa para completar un bloque `Try...Catch...Finally`; por lo tanto, solo puede aparecer una vez al final del bloque.  
  
 **Identificador de error:** BC30381  
  
### Para corregir este error  
  
1.  Localice y quite la instrucción `Finally` redundante.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Información general sobre el control estructurado de excepciones de Visual Basic](http://msdn.microsoft.com/es-es/bb81af80-a735-4873-9711-6151a48e418a)