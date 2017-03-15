---
title: "La bifurcaci&#243;n fuera de una cl&#225;usula &#39;Finally&#39; no es v&#225;lida | Microsoft Docs"
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
  - "bc30101"
  - "vbc30101"
helpviewer_keywords: 
  - "BC30101"
ms.assetid: 16a0dc29-3657-4373-b77f-38f3cb80e6c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La bifurcaci&#243;n fuera de una cl&#225;usula &#39;Finally&#39; no es v&#225;lida
Una instrucción `GoTo` dentro de un bloque `Finally` se bifurca fuera del bloque. No es válida para la bifurcación dentro o fuera de un bloque `Catch` o `Finally`.  
  
 **Identificador de error:** BC30101  
  
### Para corregir este error  
  
-   Quite la instrucción `GoTo` y considere implementar la lógica del programa con estructuras de control de decisiones o de bucle.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [GoTo \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Flujo de control](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)