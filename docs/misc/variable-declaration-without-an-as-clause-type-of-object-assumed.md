---
title: "Declaraci&#243;n de variable sin una cl&#225;usula &#39;As&#39;; se supone el tipo de Object. | Microsoft Docs"
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
  - "BC42020"
  - "vbc42020"
helpviewer_keywords: 
  - "BC42020"
ms.assetid: 9422b16d-39b5-4d49-b697-608226ccafea
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declaraci&#243;n de variable sin una cl&#225;usula &#39;As&#39;; se supone el tipo de Object.
Una declaración de variable no especifica una cláusula `As`.  
  
 Una cláusula `As` identifica un tipo de datos que se va a asociar a un elemento de programación. En una [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement), especifica el tipo de datos de la variable o variables. Si no incluye una cláusula `As` en la instrucción `Dim`, el tipo de datos de la variable tiene `Object` como valor predeterminado.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42020  
  
### Para corregir este error  
  
-   Incluya una cláusula `As` en la instrucción `Dim` para especificar el tipo de datos de la variable.  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaración de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)