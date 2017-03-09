---
title: "La instrucci&#243;n &#39;End Select&#39; debe ir precedida de la instrucci&#243;n &#39;Select Case&#39; correspondiente | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;End Select&#39; debe ir precedida de la instrucci&#243;n &#39;Select Case&#39; correspondiente
Una instrucción `End Select` aparece sin una instrucción `Select` o `Select Case` correspondiente. La instrucción `End Select` debe ir precedida por una instrucción `Select` o `Select Case`.  
  
 **Id. de error:** BC30088  
  
### Para corregir este error  
  
1.  Si este bloque `Select` forma parte de un conjunto de bloques `Select` anidados, asegúrese de que cada bloque esté terminado correctamente.  
  
2.  Compruebe que el resto de estructuras de control dentro del bloque `Select` terminen correctamente.  
  
3.  Compruebe que este cloque `Select` tenga el formato correcto.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)