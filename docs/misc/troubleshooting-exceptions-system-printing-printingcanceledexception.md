---
title: "Soluci&#243;n de problemas de excepciones: System.Printing.PrintingCanceledException | Microsoft Docs"
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
  - "PrintingCanceledException (excepción)"
  - "System.Printing.PrintingCanceledException (excepción)"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Printing.PrintingCanceledException
Se produce una excepción <xref:System.Printing.PrintingCanceledException> cuando el código intenta obtener acceso a un trabajo de impresión cancelado.  
  
## Comentarios  
 Si crea una aplicación de Windows Presentation Foundation \(WPF\) que incluye la funcionalidad de impresión y permite que se cancelen los trabajos de impresión, asegúrese de controlar correctamente esta excepción. Una excepción de este tipo no controlada puede hacer que una aplicación de Windows Presentation Foundation deje de responder.  
  
## Vea también  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)