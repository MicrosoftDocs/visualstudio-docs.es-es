---
title: "Soluci&#243;n de problemas de excepciones: System.IO.InternalBufferOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InternalBufferOverflowException (clase)"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IO.InternalBufferOverflowException
Cuando el búfer interno se desborda, se produce una excepción <xref:System.IO.InternalBufferOverflowException>.  
  
## Sugerencias asociadas  
 **Cuando utilice FileSystemWatcher, elimine las notificaciones de cambio no deseadas.**  
 En un monitor de sistema de archivos, cuando se le notifican los cambios realizados en los archivos, el sistema almacena estos cambios en un búfer que el componente crea y pasa a las interfaces de programación de aplicaciones \(API\). Si se producen muchos cambios en poco tiempo, el búfer puede desbordarse, lo que origina una excepción <xref:System.IO.InternalBufferOverflowException> y, como consecuencia, se pierden todos los cambios. Para impedir que el búfer se desborde, utilice las propiedades <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> y <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> con objeto de filtrar las notificaciones de cambio no deseadas. Para obtener más información, consulta <xref:System.IO.FileSystemWatcher>.  
  
## Comentarios  
 También puede aumentar el tamaño del búfer interno mediante la propiedad <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A>. No obstante, un aumento del tamaño del búfer afecta al rendimiento, por lo que se recomienda utilizar el menor tamaño posible.  
  
## Vea también  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)