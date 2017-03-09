---
title: "&#39;Exit While&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;While&#39; | Microsoft Docs"
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
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit While&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;While&#39;
Una instrucción `Exit While` aparece fuera de un bloque `While`.`Exit While` solo es válida entre una instrucción `While` y su instrucción `End While` correspondiente.  
  
 **Id. de error:** BC30097  
  
### Para corregir este error  
  
1.  Asegúrese de que una instrucción `While` válida precede a `Exit While`, y de que una instrucción `End While` válida aparece después.  
  
2.  Compruebe que el resto de estructuras de control dentro del bloque `While` terminen correctamente.  
  
## Vea también  
 [While...End While \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)