---
title: "Soluci&#243;n de problemas de excepciones: System.Reflection.TargetException | Microsoft Docs"
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
  - "System.Reflection.TargetException (excepción)"
  - "TargetException (excepción)"
ms.assetid: 88b8e4b4-f1a3-4c4a-b1ef-cac176160803
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Reflection.TargetException
La excepción que se produce cuando se intenta invocar un destino no válido.  
  
## Comentarios  
 Se produce una excepción <xref:System.Reflection.TargetException> cuando se intenta invocar un método no estático en un objeto null. Puede producirse porque el llamante no tiene acceso al miembro, porque el destino no define el miembro, o por circunstancias similares.  
  
## Vea también  
 <xref:System.Reflection.TargetException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)