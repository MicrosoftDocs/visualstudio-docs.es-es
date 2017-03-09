---
title: "&#39;Select Case&#39; debe terminar con una instrucci&#243;n &#39;End Select&#39; coincidente. | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; debe terminar con una instrucci&#243;n &#39;End Select&#39; coincidente.
Una instrucción `Select` o `Select Case` aparece sin una instrucción `End Select` correspondiente. Una instrucción `End Select` debe usarse para finalizar el bloque `Select`.  
  
 **Identificador de error:** BC30095  
  
### Para corregir este error  
  
1.  Si este bloque `Select` forma parte de un conjunto de bloques `Select` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Agregue una instrucción `End Select` al final del bloque `Select`.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)