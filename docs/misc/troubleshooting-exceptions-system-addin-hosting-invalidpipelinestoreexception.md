---
title: "Soluci&#243;n de problemas de excepciones: System.AddIn.Hosting.InvalidPipelineStoreException | Microsoft Docs"
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
  - "InvalidPipelineStoreException (excepción)"
  - "System.AddIn.Hosting.InvalidPipelineStoreException (excepción)"
ms.assetid: d12556bc-5cfd-481c-a27b-46ee2571e646
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.AddIn.Hosting.InvalidPipelineStoreException
Se produce la excepción <xref:System.AddIn.Hosting.InvalidPipelineStoreException> cuando no se encuentra un directorio y el usuario no tiene permiso para obtener acceso a la ruta raíz de la canalización ni a la ruta de un complemento.  
  
## Comentarios  
 A diferencia de <xref:System.IO.DirectoryNotFoundException>, esta excepción no proporciona ninguna información sobre la ruta de acceso. Esto evita que un usuario malintencionado pueda especificar deliberadamente rutas de acceso erróneas y utilizar la información que devuelve la excepción para determinar las rutas de acceso correctas.  
  
 Esta excepción la producen los siguientes métodos de detección que compilan y actualizan el almacén de información de canalización y complementos: <xref:System.AddIn.Hosting.AddInStore.FindAddIns%2A>,<xref:System.AddIn.Hosting.AddInStore.Rebuild%2A>, <xref:System.AddIn.Hosting.AddInStore.RebuildAddIns%2A>, <xref:System.AddIn.Hosting.AddInStore.Update%2A> y <xref:System.AddIn.Hosting.AddInStore.UpdateAddIns%2A>.  
  
## Vea también  
 <xref:System.AddIn.Hosting.InvalidPipelineStoreException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)