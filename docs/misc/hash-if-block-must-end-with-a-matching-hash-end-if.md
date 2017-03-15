---
title: "El bloque &#39;#If&#39; debe terminar con la instrucci&#243;n &#39;#End If&#39; correspondiente | Microsoft Docs"
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
  - "vbc30012"
  - "bc30012"
helpviewer_keywords: 
  - "BC30012"
ms.assetid: 9d51f3be-d2c3-4918-a36d-0d9e9763e47b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El bloque &#39;#If&#39; debe terminar con la instrucci&#243;n &#39;#End If&#39; correspondiente
`#If` es una directiva de compilación condicional. Un bloque `#If` no termina con una directiva `#End If`.  
  
 **Id. de error:** BC30012  
  
### Para corregir este error  
  
-   Agregue una directiva `#End If` al final del bloque de compilación condicional.  
  
## Vea también  
 [\#If...Then...\#Else \(Directivas\)](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)