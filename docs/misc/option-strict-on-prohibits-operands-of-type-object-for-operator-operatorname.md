---
title: "Option Strict On proh&#237;be operandos de tipo Object para el operador &#39;&lt;nombreDeOperador&gt;&#39; | Microsoft Docs"
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
  - "bc30038"
  - "vbc30038"
helpviewer_keywords: 
  - "BC30038"
ms.assetid: eb047d36-1fb4-460d-ae98-c76f31a89bed
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On proh&#237;be operandos de tipo Object para el operador &#39;&lt;nombreDeOperador&gt;&#39;
Los únicos operadores definidos para las variables de objeto son `Is` y `TypeOf...Is`. Cuando `Option Strict` es `On`, todos los operandos deben ser tipos de datos definidos para el operador especificado.  
  
 **Identificador del error:** BC30038  
  
### Para corregir este error  
  
-   Use las funciones de conversión de tipo adecuadas, como `CInt` o `CStr`, para convertir los operandos en tipos de datos definidos para el operador.  
  
## Vea también  
 [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)