---
title: "&#39;Exit&#39; debe ir seguida de &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; o &#39;Try&#39;. | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit&#39; debe ir seguida de &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; o &#39;Try&#39;.
Una instrucción `Exit` contiene una palabra clave no válida.`Exit` debe especificar el bloque desde el que se transferirá a la instrucción que sigue al bloque; por ejemplo, `End While`.  
  
 **Identificador de error:** BC30240  
  
### Para corregir este error  
  
-   Agregue una palabra clave válida después de `Exit`, o quite la instrucción `Exit`.  
  
## Vea también  
 [Exit \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/exit-statement)