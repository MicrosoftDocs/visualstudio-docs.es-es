---
title: "El nombre de origen especificado en EventLogSource se registra en un registro distinto del especificado en EventLogName. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre de origen especificado en EventLogSource se registra en un registro distinto del especificado en EventLogName.
El `EventLog` intenta hacer referencia a un origen que está registrado en un registro diferente. Si va a escribir entradas en un registro de eventos, debe especificar la propiedad <xref:System.Diagnostics.EventLog.Source%2A>. La propiedad <xref:System.Diagnostics.EventLog.Source%2A> registra el componente con el registro de eventos como un origen válido de entradas. Un origen único se puede asociar \(y, por tanto, escribir entradas\) con un único registro de eventos a la vez.  
  
 De forma predeterminada, si intenta escribir una entrada sin haber registrado primero el componente como un origen válido, el sistema automáticamente registrará el origen con el registro de eventos, usando el valor de la propiedad <xref:System.Diagnostics.EventLog.Source%2A> como la cadena de origen.  
  
### Para corregir este error  
  
-   Asegúrese de que el origen está registrado en el registro correcto. Para ello, use el método <xref:System.Diagnostics.EventLog.CreateEventSource%2A> o una de sus sobrecargas para especificar una cadena que identifique de forma única el componente en el registro de eventos.  
  
## Vea también  
 [Administering Event Logs](http://msdn.microsoft.com/es-es/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/es-es/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/es-es/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/es-es/bc66c900-4b8a-426a-b8e2-17031a20167e)