---
title: "Se han utilizado operandos del tipo Object en expresiones de instrucciones &#39;Select&#39;, &#39;Case&#39;. Podr&#237;an producirse errores en tiempo de ejecuci&#243;n. | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se han utilizado operandos del tipo Object en expresiones de instrucciones &#39;Select&#39;, &#39;Case&#39;. Podr&#237;an producirse errores en tiempo de ejecuci&#243;n.
Una construcción `Select`...`Case` usa una o varias expresiones del [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Si una variable o expresión se evalúa como `Object`, el compilador debe realizar el *enlace en tiempo de ejecución*, que produce operaciones adicionales en tiempo de ejecución. También expone la aplicación a posibles errores en tiempo de ejecución. Por ejemplo, si asigna un <xref:System.Windows.Forms.Form> a una variable `Object` e intenta usarlo para compararlo con un número, el tiempo de ejecución produce una <xref:System.InvalidCastException> porque Visual Basic no puede convertir un objeto <xref:System.Windows.Forms.Form> en un valor numérico.  
  
 Las expresiones de una construcción `Select`...`Case` deben ser todas del mismo tipo de datos o de tipos de datos estrechamente relacionados que se puedan convertir entre sí. Esto se debe a que cada instrucción `Case` compara al menos un valor con la expresión de prueba en la que se basa la construcción `Select`...`Case`.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42036  
  
### Para corregir este error  
  
-   Si es posible, organice todas las expresiones que se van a evaluar como tipos de datos con operadores de comparación definidos.  
  
## Vea también  
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Operadores aritméticos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)