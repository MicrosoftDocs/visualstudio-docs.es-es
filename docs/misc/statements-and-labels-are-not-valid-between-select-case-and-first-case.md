---
title: "Las instrucciones y etiquetas no son v&#225;lidas entre &#39;Select Case&#39; y la primera instrucci&#243;n &#39;Case&#39; | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones y etiquetas no son v&#225;lidas entre &#39;Select Case&#39; y la primera instrucci&#243;n &#39;Case&#39;
Una instrucción que no es un comentario aparece entre la instrucción de apertura `Select` o `Select Case` y su primera instrucción `Case`.  
  
 **Identificador de error:** BC30058  
  
### Para corregir este error  
  
-   Si la instrucción que interviene es un comentario, debe ir precedida por un delimitador de comentario \(`'` o `REM`\). En caso contrario, mueva o elimine la instrucción.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)