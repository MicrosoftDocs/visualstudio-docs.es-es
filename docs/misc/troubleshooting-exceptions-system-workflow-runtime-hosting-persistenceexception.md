---
title: "Soluci&#243;n de problemas de excepciones: System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException (excepción)"
  - "System.Workflow.Runtime.Hosting.PersistenceException (excepción)"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Workflow.Runtime.Hosting.PersistenceException
Se produce una excepción <xref:System.Workflow.Runtime.Hosting.PersistenceException> cuando el servicio de persistencia no puede cumplir una solicitud.  
  
## Comentarios  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> produce una excepción <xref:System.Workflow.Runtime.Hosting.PersistenceException> si no puede completar una solicitud para confirmar un ámbito completado o el estado de la instancia de flujo de trabajo a su base de datos.  
  
 Si implementa un servicio de persistencia derivando de la clase <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> o <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, puede producir la excepción <xref:System.Workflow.Runtime.Hosting.PersistenceException> con un mensaje adecuado para indicar cualquier condición de error detectada por el servicio que le impida cumplir una solicitud realizada por el motor en tiempo de ejecución de flujo de trabajo.  
  
 Vea <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> para obtener más información.  
  
## Vea también  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)