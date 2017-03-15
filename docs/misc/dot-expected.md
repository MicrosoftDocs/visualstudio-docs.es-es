---
title: "Se esperaba &#39;.&#39; | Microsoft Docs"
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
  - "bc30287"
  - "vbc30287"
helpviewer_keywords: 
  - "BC30287"
ms.assetid: 7d7b4934-b521-4ed3-b054-aeb71f8daacf
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;.&#39;
El código tiene una cláusula `Handles` que contiene un signo de exclamación \(`!`\).  
  
 **Identificador de error:** BC30287  
  
### Para corregir este error  
  
1.  Si la cláusula `Handles` hace referencia a un evento dentro de un objeto, use un punto \(`.`\) para separar el objeto del evento.  
  
     Este ejemplo administra el evento `Click` desde el objeto `Button1`.  
  
     [!code-vb[VbVbalrEventError#21](../misc/codesnippet/VisualBasic/dot-expected_1.vb)]  
  
## Vea también  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)