---
title: "&#39;End With&#39; debe ir precedida de la instrucci&#243;n &#39;With&#39; correspondiente. | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; debe ir precedida de la instrucci&#243;n &#39;With&#39; correspondiente.
Una instrucción `End With` aparece sin una instrucción `With` correspondiente.`End With` debe ir precedida de una instrucción `With` correspondiente.  
  
 **Identificador de error:** BC30093  
  
### Para corregir este error  
  
1.  Si este bloque `With` forma parte de un conjunto de bloques `With` anidados, asegúrese de que cada bloque está terminado correctamente.  
  
2.  Compruebe que el resto de estructuras de control dentro del bloque `With` están terminadas correctamente.  
  
3.  Asegúrese de que este bloque `With` tenga el formato correcto.  
  
## Vea también  
 [With...End With \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)