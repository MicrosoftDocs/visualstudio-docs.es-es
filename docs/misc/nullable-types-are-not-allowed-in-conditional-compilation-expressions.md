---
title: "No se permiten tipos que acepten valores NULL en expresiones de compilaci&#243;n condicionales | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permiten tipos que acepten valores NULL en expresiones de compilaci&#243;n condicionales
No se puede usar un tipo que acepta valores NULL en la expresión de una directiva de compilación condicional. Por ejemplo, el código siguiente causa este error.  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **Identificador de error:** BC33111  
  
### Para corregir este error  
  
-   Quite la designación que acepta valores NULL.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [\#If...Then...\#Else \(Directivas\)](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)   
 [Compilación condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)