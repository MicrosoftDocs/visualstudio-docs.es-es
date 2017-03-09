---
title: "Otro registro de eventos ya ha registrado un origen con este nombre. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Otro registro de eventos ya ha registrado un origen con este nombre.
Se ha intentado escribir una entrada en un registro de eventos donde el origen especificado está registrado con otro registro de eventos.  
  
 Debe establecer la propiedad <xref:System.Diagnostics.EventLog.Source%2A> de la instancia de componente <xref:System.Diagnostics.EventLog> antes de que el componente escriba una entrada en un registro. Cuando ocurre esto, el sistema comprueba que el origen especificado está registrado con el registro de eventos en el que el componente está escribiendo y llama a <xref:System.Diagnostics.EventLog.CreateEventSource%2A>, si es necesario.  
  
### Para corregir este error  
  
1.  Elimine la asociación del origen con el primer registro mediante el método <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>.  
  
2.  Registre el origen con el nuevo registro.  
  
## Vea también  
 [My.Application.Log \(Objeto\)](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/es-es/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/es-es/948ff920-a739-4e66-a191-ee951512d42c)