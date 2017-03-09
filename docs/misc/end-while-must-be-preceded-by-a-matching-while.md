---
title: "&#39;End While&#39; debe ir precedida de la instrucci&#243;n &#39;While&#39; correspondiente | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; debe ir precedida de la instrucci&#243;n &#39;While&#39; correspondiente
Una instrucción `End While` aparece sin una instrucción `While` correspondiente.`End While` debe ir precedida de una instrucción `While` correspondiente.  
  
 **Identificador de error:** BC30090  
  
### Para corregir este error  
  
1.  Si este bloque `While` forma parte de un conjunto de bloques `While` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Compruebe que el resto de las estructuras de control dentro del bloque `While` terminen correctamente.  
  
3.  Asegúrese de que este bloque `While` tenga el formato correcto.  
  
## Vea también  
 [While...End While \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)