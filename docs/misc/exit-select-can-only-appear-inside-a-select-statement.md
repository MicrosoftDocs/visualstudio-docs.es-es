---
title: "&#39;Exit Select&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select&#39; | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Select&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;Select&#39;
Una instrucción `Exit Select` aparece fuera de un bloque `Select`.`Exit Select` solo es válida entre una instrucción `Select` o `Select Case` y su instrucción `End Select` correspondiente.  
  
 **Id. de error:** BC30099  
  
### Para corregir este error  
  
1.  Asegúrese de que una instrucción `Select` o `Select Case` válida preceda a `Exit Select`, y de que una instrucción `End Select` válida aparezca después.  
  
2.  Compruebe que el resto de estructuras de control dentro del bloque `Select` terminen correctamente.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)