---
title: "Operador sin una cl&#225;usula &#39;As&#39;; se supone el tipo de Object. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador sin una cl&#225;usula &#39;As&#39;; se supone el tipo de Object.
Un procedimiento de operador no especifica una cláusula `As`.  
  
 Una cláusula `As` identifica un tipo de datos que se debe asociar a un elemento de programación. En un elemento [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement), especifica el tipo de datos del valor que el procedimiento del operador devuelve al código de llamada. Si no incluye una cláusula `As` en la instrucción `Operator`, el tipo de datos devuelto es `Object` de forma predeterminada.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC41005  
  
### Para corregir este error  
  
-   Incluya una cláusula `As` en la instrucción `Operator` para especificar el tipo de datos devuelto.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)