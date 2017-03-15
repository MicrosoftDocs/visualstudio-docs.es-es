---
title: "&#39;For&#39; debe terminar con la instrucci&#243;n &#39;Next&#39; correspondiente | Microsoft Docs"
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
  - "vbc30084"
  - "bc30084"
helpviewer_keywords: 
  - "BC30084"
ms.assetid: 4c5e49c2-7343-4487-b5f8-a38c97ba895b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For&#39; debe terminar con la instrucci&#243;n &#39;Next&#39; correspondiente
Una instrucción `For` aparece sin su instrucción `Next` correspondiente. Una instrucción `Next` debe usarse para finalizar el bucle `For`.  
  
 **Identificador de error:** BC30084  
  
### Para corregir este error  
  
-   Si este bucle `For` forma parte de un conjunto de bucles anidados, asegúrese de que cada bucle esté terminado correctamente.  
  
-   Agregue una instrucción `Next` al final del bucle `For`.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)