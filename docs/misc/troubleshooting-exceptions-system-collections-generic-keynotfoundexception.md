---
title: "Soluci&#243;n de problemas de excepciones: System.Collections.Generic.KeyNotFoundException | Microsoft Docs"
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
  - "KeyNotFoundException (clase)"
ms.assetid: de33f5bb-5709-46fe-b889-7105dbd24299
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Collections.Generic.KeyNotFoundException
Se produce una <xref:System.Collections.Generic.KeyNotFoundException> cuando se intenta recuperar una clave o un par de valores de clave de una colección utilizando una clave no existente.  
  
## Sugerencias asociadas  
 **Compruebe que la clave que está utilizando existe en la colección que está intentando tener acceso.**  
 Esta excepción aparece cuando una operación intenta recuperar un elemento en una colección utilizando una clave que no existe en esa colección.  
  
### Comentarios  
 El método <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> se puede utilizar para determinar si una clave existe.  
  
## Vea también  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.KeyNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)