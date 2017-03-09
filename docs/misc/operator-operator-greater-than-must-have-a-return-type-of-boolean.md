---
title: "El operador &#39;&lt;operador&gt;&#39; debe tener un tipo de valor devuelto Boolean | Microsoft Docs"
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
  - "vbc33023"
  - "bc33023"
helpviewer_keywords: 
  - "BC33023"
ms.assetid: 18e066f4-d71e-4e38-b0bc-8af9145f6015
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &#39;&lt;operador&gt;&#39; debe tener un tipo de valor devuelto Boolean
Un operador lógico o de comparación está declarado con un tipo de valor devuelto distinto de [Boolean \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/boolean-data-type).  
  
 El resultado de un operador de comparación \(`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `IsFalse`, `IsTrue`, `Like`, `TypeOf`\) solo puede ser `True` o `False`. Para obtener más información, consulta [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators).  
  
 Los operadores lógicos \(`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`\) funcionan por completo dentro del dominio de valores Boolean. Para obtener más información, consulta [Operadores lógicos y bit a bit en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators).  
  
 **Identificador de error:** BC33023  
  
### Para corregir este error  
  
-   Reemplace el tipo de valor devuelto de este operador lógico o de comparación por `Boolean`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)