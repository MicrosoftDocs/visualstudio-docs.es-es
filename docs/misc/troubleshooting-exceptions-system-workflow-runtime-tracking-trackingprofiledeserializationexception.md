---
title: "Soluci&#243;n de problemas de excepciones: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException (excepción)"
  - "TrackingProfileDeserializationException (excepción)"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
Se produce una excepción <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> cuando un documento XML no ha podido ser deserializado en un <xref:System.Workflow.Runtime.Tracking.TrackingProfile> por un <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer>.  
  
## Comentarios  
 Cuando <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> produce esta excepción, proporciona un mensaje que describe la razón de la excepción. En algunos casos, <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> proporciona una lista de las advertencias y los errores de validación que ha encontrado al intentar deserializar <xref:System.Workflow.Runtime.Tracking.TrackingProfile>. Si se proporciona esta lista, la contiene la propiedad <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A>.  
  
## Vea también  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)