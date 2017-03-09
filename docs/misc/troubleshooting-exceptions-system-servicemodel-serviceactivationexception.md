---
title: "Soluci&#243;n de problemas de excepciones: System.ServiceModel.ServiceActivationException | Microsoft Docs"
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
  - "ServiceActivationException (excepción)"
  - "System.ServiceModel.ServiceActivationException (excepción)"
ms.assetid: 32a3ea87-d6da-40bf-ba04-e862ac122391
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ServiceModel.ServiceActivationException
Se produce una excepción <xref:System.ServiceModel.ServiceActivationException> cuando un servicio no se activa.  
  
## Comentarios  
 Esta excepción deriva de <xref:System.ServiceModel.CommunicationException>, que representa una clase de errores recuperables que pueden producirse durante la comunicación entre extremos y que se espera que controlen las sólidas aplicaciones cliente y de servicio de [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]. Para evitar que el controlador de la excepción <xref:System.ServiceModel.CommunicationException> más genérica detecte la <xref:System.ServiceModel.ActionNotSupportedException> más específica, detecte esta excepción antes de controlar <xref:System.ServiceModel.CommunicationException>.  
  
## Vea también  
 <xref:System.ServiceModel.ServiceActivationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)