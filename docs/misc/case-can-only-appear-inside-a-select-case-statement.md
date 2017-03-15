---
title: "&#39;Case&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select Case&#39; | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select Case&#39;
Una instrucción `Case` aparece fuera de un bloque `Select`. Una instrucción `Case` solo es válida entre una instrucción `Select` o `Select Case` y su instrucción `End Select` correspondiente.  
  
 **Identificador de error:** BC30072  
  
### Para corregir este error  
  
-   Quite la instrucción `Case` o muévala dentro de un bloque `Select`.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)