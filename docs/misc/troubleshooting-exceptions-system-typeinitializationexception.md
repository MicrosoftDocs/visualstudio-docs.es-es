---
title: "Soluci&#243;n de problemas de excepciones: System.TypeInitializationException | Microsoft Docs"
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
  - "TypeInitializationException (excepción)"
  - "System.TypeInitializationException (excepción)"
ms.assetid: c77e81fd-1518-49a1-8213-3f169658f5f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.TypeInitializationException
Excepción que se produce como contenedor de la excepción producida por el inicializador de la clase.  
  
## Comentarios  
 Cuando el inicializador de clase no logra inicializar un tipo, se crea una excepción <xref:System.TypeInitializationException> y se pasa una referencia a la excepción producida por el inicializador de clase del tipo. La propiedad <xref:System.Exception.InnerException%2A> de <xref:System.TypeInitializationException> contiene la excepción subyacente.  
  
## Vea también  
 <xref:System.TypeInitializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)