---
title: "&#39;Using&#39; debe terminar con una instrucci&#243;n &#39;End Using&#39; correspondiente | Microsoft Docs"
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
  - "vbc36008"
  - "bc36008"
helpviewer_keywords: 
  - "BC36008"
ms.assetid: 83269108-b169-40a6-bbcc-af1ac8fcfd67
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; debe terminar con una instrucci&#243;n &#39;End Using&#39; correspondiente
Una instrucción `Using` se produce sin una instrucción `End Using` correspondiente.  
  
 Una instrucción `End Using` debe usarse para finalizar el bloque `Using`.  
  
 **Identificador de error:** BC36008  
  
### Para corregir este error  
  
1.  Si este bloque `Using` forma parte de un conjunto de bloques `Using` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Agregue una instrucción `End Using` al final del bloque `Using`.  
  
## Vea también  
 [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Cómo: Deshacerse de un recurso del sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)