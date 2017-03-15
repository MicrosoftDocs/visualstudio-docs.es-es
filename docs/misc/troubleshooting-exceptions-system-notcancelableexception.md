---
title: "Soluci&#243;n de problemas de excepciones: System.NotCancelableException | Microsoft Docs"
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
  - "NotCancelableException (clase)"
ms.assetid: 36b82d4b-f075-4af5-993a-3e763a7e254a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.NotCancelableException
Cuando se intenta cancelar una operación que no se puede cancelar, se produce una excepción `NotCancelableException`.  
  
## Sugerencias asociadas  
 No intente cancelar la operación.  
 Algunas operaciones no se pueden cancelar y producirán esta excepción cuando se intenten cancelar. En estos casos, evite proporcionar al usuario una opción para cancelar la operación.  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)