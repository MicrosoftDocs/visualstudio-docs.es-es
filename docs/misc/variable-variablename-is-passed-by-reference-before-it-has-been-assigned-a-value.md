---
title: "La referencia pasa una variable &#39;&lt;nombreVariable&gt;&#39; antes de que se le haya asignado un valor. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La referencia pasa una variable &#39;&lt;nombreVariable&gt;&#39; antes de que se le haya asignado un valor.
La referencia pasa una variable '\<nombreVariable\>' antes de que se le haya asignado un valor. Podría producirse una excepción de referencia nula en tiempo de ejecución.  
  
 Una llamada a procedimiento pasa una variable como argumento para un parámetro `ByRef` antes de asignar cualquier valor a la variable.  
  
 Si nunca se ha asignado un valor a una variable, contiene el valor predeterminado para su tipo de datos. Para un tipo de datos de referencia, el valor predeterminado es [Nothing](/dotnet/visual-basic/language-reference/nothing). Leer una variable de referencia que tiene un valor de `Nothing` puede producir una excepción <xref:System.NullReferenceException> en algunas circunstancias.  
  
 Cuando se pasa un argumento a un procedimiento `ByRef`, se expone a la variable subyacente del argumento a una posible modificación por parte del procedimiento.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42030  
  
### Para corregir este error  
  
-   Si quiere que el procedimiento asigne un valor a la variable mediante el argumento `ByRef`, y si no importa si la variable ya contiene un valor, no es necesario realizar ninguna acción.  
  
-   Si la lógica del procedimiento lee el argumento antes de asignarle algún valor, y si la variable es de un tipo de valor, asegúrese de que la lógica del procedimiento no depende de si la variable contiene o no su valor predeterminado.  
  
-   Si la lógica del procedimiento lee el argumento antes de asignarle algún valor, y si la variable es de un tipo de referencia, asegúrese de que la lógica del procedimiento puede controlar un valor de `Nothing`. Por ejemplo, podría usar una [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) para detectar una excepción <xref:System.NullReferenceException>.  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Pasar argumentos por valor y por referencia](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Declaración de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [Solucionar problemas de variables](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)