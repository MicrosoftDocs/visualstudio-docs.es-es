---
title: "&#39;#ElseIf&#39;, &#39;#Else&#39; o &#39;#End If&#39; deben ir precedidas de la instrucci&#243;n &#39;#If&#39; correspondiente. | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;, &#39;#Else&#39; o &#39;#End If&#39; deben ir precedidas de la instrucci&#243;n &#39;#If&#39; correspondiente.
`#ElseIf`, `#Else` y `#End If` son directivas de compilación condicionales.`#ElseIf`, `#Else` o `#End If` no va precedida de su directiva `#If` correspondiente.  
  
 **Identificador de error:** BC30013  
  
### Para corregir este error  
  
1.  Compruebe que la directiva `#If` prevista no esté separada de la cláusula en cuestión por un bloque de compilación condicional intermedio o que una directiva `#End If` esté colocada incorrectamente.  
  
    > [!NOTE]
    >  Solo se permite una `#Else` en cada bloque `#If`, por lo que dos directivas `#Else` sucesivas producen este error.  
  
2.  Compruebe que no falta el símbolo `#` inicial en una directiva `#If` anterior.  
  
3.  Si todo lo demás es correcto, agregue una directiva `#If` al principio del bloque de compilación condicional.  
  
## Vea también  
 [\#If...Then...\#Else \(Directivas\)](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)