---
title: "&#39;TypeOf...Is&#39; requiere que el operando situado a su izquierda tenga un tipo de referencia, pero este operando tiene el tipo &#39;&lt;type&gt;&#39;. | Microsoft Docs"
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
  - "bc30021"
  - "vbc30021"
helpviewer_keywords: 
  - "BC30021"
ms.assetid: a6e76fc8-9c7f-4e55-8b68-e6e7b03a6737
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TypeOf...Is&#39; requiere que el operando situado a su izquierda tenga un tipo de referencia, pero este operando tiene el tipo &#39;&lt;type&gt;&#39;.
La expresión `TypeOf...Is` comprueba la compatibilidad de tipo de tiempo de ejecución de una variable de objeto. Esta compatibilidad no está definida para los tipos de valor.  
  
 **Identificador de error:** BC30021  
  
### Para corregir este error  
  
-   Si `Option Strict` es `Off`, use la función `TypeName` o `VarType` para obtener información sobrel el tipo de datos de la variable.  
  
-   Si `Option Strict` es `On`, la declaración de variable determina el tipo de datos de la variable.  
  
## Vea también  
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [NO ESTÁ EN LA COMPILACIÓN: Función TypeName \(Visual Basic\)](http://msdn.microsoft.com/es-es/6197bc6c-e8a6-4711-883c-0c95e94e272c)   
 [NO ESTÁ EN LA COMPILACIÓN: Función VarType \(Visual Basic\)](http://msdn.microsoft.com/es-es/e820b6fc-faa6-4de4-836a-0466032dc190)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)