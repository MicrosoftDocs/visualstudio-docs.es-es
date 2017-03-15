---
title: "Los operadores de conversi&#243;n no se pueden convertir en un tipo de interfaz | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33025"
  - "bc33025"
helpviewer_keywords: 
  - "BC33025"
ms.assetid: 7e13dfa3-2b70-4ca6-a8ec-159131fd2c4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores de conversi&#243;n no se pueden convertir en un tipo de interfaz
Un operador de conversión está declarado con un tipo de interfaz como un tipo de valor devuelto.  
  
 En tiempo de compilación, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera que existe una conversión predefinida desde cualquier tipo de referencia a cualquier interfaz. Este tipo de conversión puede producir un error en tiempo de ejecución, pero el compilador no puede predecir los resultados en tiempo de ejecución, por lo que permite que estas conversiones se compilen.  
  
 Dado que el compilador considera que esta conversión ya está definida, no permite redefinirla.  
  
 **Identificador de error:** BC33025  
  
### Para corregir este error  
  
-   Quite completamente esta definición de operador. Ya está predefinido.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)