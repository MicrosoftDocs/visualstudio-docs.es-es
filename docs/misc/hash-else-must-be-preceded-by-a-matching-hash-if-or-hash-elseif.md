---
title: "&#39;#Else&#39; debe precederse de un elemento &#39;#If&#39; o &#39;#ElseIf&#39; correspondiente | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Else&#39; debe precederse de un elemento &#39;#If&#39; o &#39;#ElseIf&#39; correspondiente
`#Else` es una directiva de compilación condicional. Una directiva `#Else` no está precedida de una directiva `#If` o `#ElseIf` correspondiente.  
  
 **Id. de error:** BC30028  
  
### Para corregir este error  
  
1.  Compruebe que el elemento `#If` o `#ElseIf` anterior no esté separado de este elemento `#Else` mediante un bloque de compilación condicional intermedio o que un elemento `#End If` colocado incorrectamente.  
  
2.  Compruebe que el elemento `#Else` está precedido por otra directiva `#Else`. Si es así, quite `#Else` o cámbielo por un elemento `#ElseIf`.  
  
3.  Si todo lo demás es correcto, agregue una directiva `#If` al principio del bloque de compilación condicional.  
  
## Vea también  
 [\#If...Then...\#Else \(Directivas\)](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)