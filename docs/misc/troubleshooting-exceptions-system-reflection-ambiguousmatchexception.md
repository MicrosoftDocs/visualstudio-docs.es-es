---
title: "Soluci&#243;n de problemas de excepciones: System.Reflection.AmbiguousMatchException | Microsoft Docs"
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
  - "System.Reflection.AmbiguousMatchException (excepción)"
  - "AmbiguousMatchException (excepción)"
ms.assetid: f92b5c51-42b6-4c2e-83df-0d598b3b41c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Reflection.AmbiguousMatchException
La excepción que se produce al enlazarse a un método hace que más de un método coincida con los criterios obligatorios.  
  
## Comentarios  
 Se produce una <xref:System.Reflection.AmbiguousMatchException> si la aplicación llama una clase y no puede determinar la clase o clase sobrecargada que debe utilizar. Los intentos obligatorios para buscar la clase apropiada que debe utilizarse, determinados por el número y el tipo de parámetros. Si se encuentran varias clases aceptables, se produce esta excepción.  
  
## Vea también  
 <xref:System.Reflection.AmbiguousMatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)