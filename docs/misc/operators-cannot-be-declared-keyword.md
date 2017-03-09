---
title: "Los operadores no se pueden declarar &#39;&lt;palabraClave&gt;&#39;. | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores no se pueden declarar &#39;&lt;palabraClave&gt;&#39;.
Un operador está declarado con una palabra clave que no es válida para las definiciones de operador.  
  
 Cada operador debe declararse como [Public](/dotnet/visual-basic/language-reference/modifiers/public) y [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Además, un operador de conversión se debe declarar con [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), pero no con ambos. Una definición de operador puede incluir opcionalmente las palabras clave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) y [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). No se permiten otras palabras clave en una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **Identificador de error:** BC33013  
  
### Para corregir este error  
  
-   Quite la palabra clave no válida de la definición de operador.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)