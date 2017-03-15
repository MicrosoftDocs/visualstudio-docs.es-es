---
title: "Soluci&#243;n de problemas de excepciones: System.OperationCanceledException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OperationCanceledException (clase)"
ms.assetid: 275e2887-7491-432b-9b80-a21bb794be29
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.OperationCanceledException
Se produce <xref:System.OperationCanceledException> cuando se realiza una operación con <xref:Microsoft.VisualBasic.FileIO.UICancelOption> establecido en `ThrowException` y la operación se cancela.  
  
## Sugerencias asociadas  
 Si prefiere que no se produzca esta excepción, establezca <xref:System.OperationCanceledException> en `DoNothing`.  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption> tiene un valor predeterminado de `ThrowException`. Si desea que no se produzca esta excepción cuando el usuario cancela la operación, establezca el valor de enumeración en `DoNothing`.  
  
## Vea también  
 <xref:System.OperationCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)