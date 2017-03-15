---
title: "Soluci&#243;n de problemas de excepciones: System.Windows.Xps.XpsWriterException | Microsoft Docs"
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
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException (excepción)"
  - "XpsWriterException (excepción)"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Windows.Xps.XpsWriterException
Se produce una excepción <xref:System.Windows.Xps.XpsWriterException> cuando se llama a un método de un objeto <xref:System.Windows.Xps.XpsDocumentWriter> o <xref:System.Windows.Xps.VisualsToXpsDocument> que no es compatible con el estado actual del objeto.  
  
## Comentarios  
 Por ejemplo, se produce esta excepción si se llama al método `CancelAsync` de cualquier tipo de objeto cuando el objeto no está realizando una operación de escritura asincrónica.  
  
## Vea también  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)