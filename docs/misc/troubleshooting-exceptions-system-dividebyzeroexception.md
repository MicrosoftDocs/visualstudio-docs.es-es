---
title: "Soluci&#243;n de problemas de excepciones: System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DivideByZeroException (clase)"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.DivideByZeroException
Se produce una excepción <xref:System.DivideByZeroException> cuando se intenta dividir un entero o un valor decimal por cero.  
  
## Sugerencias asociadas  
 **Asegúrese de que el valor del denominador no es cero antes de realizar una operación de división.**  
 La división de un valor de punto flotante por cero da como resultado un valor infinito positivo, infinito negativo o No es un número \(NaN\), de acuerdo con las normas aritméticas de IEEE. Las operaciones de punto flotante nunca producen una excepción.  
  
## Vea también  
 <xref:System.DivideByZeroException>   
 [Operadores aritméticos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)