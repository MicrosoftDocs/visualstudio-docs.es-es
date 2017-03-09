---
title: "Solo los operadores de conversi&#243;n se pueden declarar como &#39;&lt;palabra clave&gt;&#39;. | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solo los operadores de conversi&#243;n se pueden declarar como &#39;&lt;palabra clave&gt;&#39;.
Una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) cuando el operador no es un operador de conversión.  
  
 Cada operador debe declararse como [Public](/dotnet/visual-basic/language-reference/modifiers/public) y [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Sin embargo, solo se puede declarar un operador de conversión con [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing), pero no ambos.  
  
 Una definición de operador puede incluir opcionalmente las palabras clave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) y [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). No hay otras palabras clave permitidas en una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **Identificador de error:** BC33019  
  
### Para corregir este error  
  
1.  Quite la palabra clave `Widening` o `Narrowing` de la definición del operador. No se aplican porque no se realiza ninguna conversión de tipos.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Conversiones de tipos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)