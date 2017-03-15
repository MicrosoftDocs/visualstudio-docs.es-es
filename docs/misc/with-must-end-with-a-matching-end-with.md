---
title: "&#39;With&#39; debe terminar con la instrucci&#243;n &#39;End With&#39; correspondiente. | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;With&#39; debe terminar con la instrucci&#243;n &#39;End With&#39; correspondiente.
Una instrucción `With` se produce sin su instrucción `End With` correspondiente. Una instrucción `End With` debe usarse para finalizar el bloque `With`.  
  
 **Identificador de error:** BC30085  
  
### Para corregir este error  
  
-   Si este bloque `With` forma parte de un conjunto de bloques `With` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
-   Agregue una instrucción `End With` al final del bloque `With`.  
  
## Vea también  
 [With...End With \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)