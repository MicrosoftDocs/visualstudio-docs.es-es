---
title: "Soluci&#243;n de problemas de excepciones: System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException (excepción)"
  - "EventDeliveryFailedException (excepción)"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Workflow.Activities.EventDeliveryFailedException
Se produce una excepción <xref:System.Workflow.Activities.EventDeliveryFailedException> cuando un evento provocado desde el host no se puede entregar a la instancia de flujo de trabajo. Normalmente, el evento se provoca desde un objeto <xref:System.Workflow.Activities.ExternalDataExchangeService> en una instancia de flujo de trabajo. Esta clase no puede heredarse.  
  
## Comentarios  
 La cadena siguiente se agrega al registro de eventos cuando se produce esta excepción: `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`.  
  
 Cuando se utiliza un flujo de trabajo de equipo de estado, puede obtener una excepción con el mensaje `Queue '{0}' is not enabled`. Esto ocurre cuando el estado actual del equipo de estado no puede controlar un evento específico. Por ejemplo, el mensaje aparece cuando un estado que no sea el actual contiene el objeto <xref:System.Workflow.Activities.EventDrivenActivity> que contiene el objeto <xref:System.Workflow.Activities.HandleExternalEventActivity> representado por la cola `'{0}'`.  
  
## Vea también  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)