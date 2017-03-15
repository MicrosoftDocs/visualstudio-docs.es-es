---
title: "Los operadores de conversi&#243;n no pueden convertir desde un tipo derivado. | Microsoft Docs"
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
  - "bc33031"
  - "vbc33031"
helpviewer_keywords: 
  - "BC33031"
ms.assetid: e8cfef89-9fde-4f33-ab0d-cc2094e8b8eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operadores de conversi&#243;n no pueden convertir desde un tipo derivado.
Un operador de conversión se declara con un tipo de parámetro que se deriva del tipo de valor devuelto.  
  
 En el tiempo de compilación, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] considera que existe una conversión predefinida desde cualquier tipo de referencia a cualquier tipo de su jerarquía de herencia, es decir, cualquier tipo del que deriva o derivado de este. Este tipo de conversión puede producir un error en tiempo de ejecución, pero el compilador no puede predecir los resultados en tiempo de ejecución, por lo que permite que estas conversiones se compilen.  
  
 Dado que el compilador considera que esta conversión ya está definida, no permite la redefinición.  
  
 **Identificador de error:** BC33031  
  
### Para corregir este error  
  
-   Quite completamente esta definición de operador. Ya está predefinido.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)