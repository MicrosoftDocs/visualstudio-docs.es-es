---
title: "&#39;ElseIf&#39; debe ir precedido de una instrucci&#243;n &#39;If&#39; o &#39;ElseIf&#39; | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ElseIf&#39; debe ir precedido de una instrucci&#243;n &#39;If&#39; o &#39;ElseIf&#39;
Una instrucción `ElseIf` se produce sin una instrucción `If` correspondiente.`ElseIf` debe ir precedido de una instrucción `If` u otra instrucción `ElseIf`.  
  
 **Identificador de error:** BC36005  
  
### Para corregir este error  
  
1.  Si este bloque `If` forma parte de un conjunto de estructuras de control anidadas, asegúrese de que cada estructura esté correctamente terminada.  
  
2.  Compruebe que otras estructuras de control anidadas dentro de este bloque `If` estén correctamente terminadas.  
  
3.  Asegúrese de que este bloque `If` tenga el formato correcto.  
  
## Vea también  
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Estructuras de decisión](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)