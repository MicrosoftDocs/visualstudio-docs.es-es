---
title: "Soluci&#243;n de problemas de excepciones: System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException (excepción)"
  - "ServerTooBusyException (excepción)"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ServiceModel.ServerTooBusyException
Se produce una excepción <xref:System.ServiceModel.ServerTooBusyException> cuando un servidor está demasiado ocupado para aceptar un mensaje.  
  
## Comentarios  
 Esta excepción deriva de <xref:System.ServiceModel.CommunicationException>, que representa una clase de errores recuperables que pueden producirse durante la comunicación entre extremos. Se espera que controlen estas excepciones las sólidas aplicaciones cliente y de servicio de [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]. Para evitar que un controlador de <xref:System.ServiceModel.CommunicationException> detecte la excepción <xref:System.ServiceModel.ServerTooBusyException> más específica, detecte esta excepción antes de controlar <xref:System.ServiceModel.CommunicationException>.  
  
## Vea también  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)