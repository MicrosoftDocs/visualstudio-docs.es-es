---
title: "Funci&#243;n sin una cl&#225;usula &#39;As&#39;; se supone un tipo de valor devuelto de Object | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Funci&#243;n sin una cl&#225;usula &#39;As&#39;; se supone un tipo de valor devuelto de Object
Un procedimiento `Function` no especifica una cláusula `As`.  
  
 Una cláusula `As` identifica un tipo de datos que se debe asociar a un elemento de programación. En un elemento [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement), especifica el tipo de datos del valor que el procedimiento `Function` devuelve al código de llamada. Si no incluye una cláusula `As` en la instrucción `Function`, el tipo de datos devuelto es `Object` de forma predeterminada.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42021  
  
### Para corregir este error  
  
-   Incluya una cláusula `As` en la instrucción `Function` para especificar el tipo de datos devuelto.  
  
## Vea también  
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)