---
title: "&#39;#ElseIf&#39; no puede ir detr&#225;s de &#39;#Else&#39; como parte de un bloque &#39;#If&#39;. | Microsoft Docs"
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
  - "bc32030"
  - "vbc32030"
helpviewer_keywords: 
  - "BC32030"
ms.assetid: 248d6464-3019-4753-8a33-7070bbe5d2a6
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; no puede ir detr&#225;s de &#39;#Else&#39; como parte de un bloque &#39;#If&#39;.
Una directiva de compilación condicional `#ElseIf` sigue a una directiva `#Else`.`#Else` debe ser la última directiva del bloque condicional antes de la directiva `#End If`.  
  
 **Identificador de error:** BC32030  
  
### Para corregir este error  
  
1.  Compruebe si la directiva `#Else` precedente debe ser una directiva `#ElseIf`.  
  
2.  Compruebe que un bloque `#If` precedente esté terminado correctamente y que se inicie un nuevo bloque `#If`.  
  
3.  Si todo lo demás es correcto, mueva esta directiva `#ElseIf` y su bloque de instrucciones correspondiente para que preceda al bloque `#Else`.  
  
## Vea también  
 [\#If...Then...\#Else \(Directivas\)](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)