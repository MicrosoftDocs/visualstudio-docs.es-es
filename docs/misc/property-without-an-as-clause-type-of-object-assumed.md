---
title: "La propiedad no tiene una cl&#225;usula &#39;As&#39;; se supone el tipo de Object | Microsoft Docs"
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
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad no tiene una cl&#225;usula &#39;As&#39;; se supone el tipo de Object
Una declaración de propiedad no especifica una cláusula `As`.  
  
 Una cláusula `As` identifica un tipo de datos que se asociará a un elemento de programación. En un elemento [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement), especifica el tipo de datos del valor que el procedimiento `Get` de la propiedad devuelve al código de llamada. Si no incluye una cláusula `As` en la instrucción `Property`, el tipo de datos de la propiedad tiene `Object` como valor predeterminado.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC42022  
  
### Para corregir este error  
  
-   Incluya una cláusula `As` en la instrucción `Property` para especificar el tipo de datos de la propiedad.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)