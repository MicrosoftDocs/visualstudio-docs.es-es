---
title: "Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "ServiceBusyException (excepción)"
  - "System.IdentityModel.Selectors.ServiceBusyException (excepción)"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.ServiceBusyException
Se produce una excepción <xref:System.IdentityModel.Selectors.ServiceBusyException> para indicar que el servicio CardSpace está ocupado procesando otras solicitudes. CardSpace no pone solicitudes en la cola y no puede dar servicio a más de una solicitud a la vez.  
  
 Determina si hay otra instancia de CardSpace en ejecución. Si hay otro instancia ejecutándose, finalícela deteniendo el proceso icardagt.exe desde el Administrador de tareas.  
  
## Vea también  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)