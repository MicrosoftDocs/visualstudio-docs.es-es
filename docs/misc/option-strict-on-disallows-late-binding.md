---
title: "Option Strict On no permite el enlace en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "bc30574"
  - "vbc30574"
helpviewer_keywords: 
  - "BC30574"
ms.assetid: 9da4b826-2e12-4a5d-9e17-762b0b68fc9b
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite el enlace en tiempo de ejecuci&#243;n
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] permite conversiones implícitas de cualquier tipo de datos a cualquier otro tipo de datos. Sin embargo, pueden perderse datos si el valor de un tipo de datos se convierte en un tipo de datos con menor precisión o menor capacidad.`Option Strict On` garantiza la notificación en tiempo de compilación de estos tipos de conversiones para que se puedan evitar. No se puede utilizar `Option Strict On` con el enlace en tiempo de ejecución.  
  
 En el ejemplo de código siguiente se utiliza el enlace en tiempo de ejecución y se produce este error cuando `Option Strict` se establece en `On`.  
  
 [!CODE [VbVbalrOptionStrictError#1](VbVbalrOptionStrictError#1)]  
  
 **Id. de error:** BC30574  
  
### Para corregir este error  
  
-   Modifique la declaración del objeto para utilizar un tipo explícito, como se muestra en el ejemplo siguiente:  
  
     [!CODE [VbVbalrOptionStrictError#2](VbVbalrOptionStrictError#2)]  
  
 O bien  
  
-   Modifique la expresión en tiempo de ejecución para especificar un tipo explícito, como se muestra en el ejemplo siguiente:  
  
     [!CODE [VbVbalrOptionStrictError#3](VbVbalrOptionStrictError#3)]  
  
 O bien  
  
-   Permita que el compilador deduzca un tipo específico, como se muestra en el ejemplo siguiente:  
  
     [!CODE [VbVbalrOptionStrictError#4](VbVbalrOptionStrictError#4)]  
  
 O bien  
  
-   Desactive `Option Strict` quitando la palabra `On` después de él o especificando `Off` explícitamente.  
  
## Vea también  
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)