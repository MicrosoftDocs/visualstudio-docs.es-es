---
title: "El operando de eventos de la instrucci&#243;n &#39;AddHandler&#39; o &#39;RemoveHandler&#39; debe ser una expresi&#243;n calificada por puntos o un nombre simple. | Microsoft Docs"
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
  - "vbc30677"
  - "bc30677"
helpviewer_keywords: 
  - "BC30677"
ms.assetid: b71eb2f0-0bb2-4aeb-94ec-5c37ab960d9e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando de eventos de la instrucci&#243;n &#39;AddHandler&#39; o &#39;RemoveHandler&#39; debe ser una expresi&#243;n calificada por puntos o un nombre simple.
El elemento especificado para el argumento de evento en `AddHandler` o `RemoveHandler` no se reconoce como un evento.  
  
 **Identificador de error:** BC30677  
  
### Para corregir este error  
  
-   Especifique el nombre del objeto que provoca el evento seguido por un punto \(`.`\) y el nombre del evento como en el ejemplo siguiente.  
  
     [!code-vb[VbVbalrEventError#30](../misc/codesnippet/VisualBasic/addhandler-or-removehandler-statement-event-operand-must-be-a-dot-qualified-expression-or-a-simple-name_1.vb)]  
  
## Vea también  
 [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: AddHandler y RemoveHandler](http://msdn.microsoft.com/es-es/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)