---
title: "&#39;Exit Do&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Do&#39;. | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Do&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Do&#39;.
Una instrucción `Exit Do` aparece fuera de un bucle `Do`.`Exit Do` solo es válida entre una instrucción `Do` y su instrucción `Loop` correspondiente.  
  
 **Identificador de error:** BC30089  
  
### Para corregir este error  
  
1.  Asegúrese de que una instrucción `Do` válida precede a `Exit Do`, y de que una instrucción `Loop` válida aparece después.  
  
2.  Compruebe que el resto de estructuras de control dentro del bucle `Do` terminen correctamente.  
  
## Vea también  
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)