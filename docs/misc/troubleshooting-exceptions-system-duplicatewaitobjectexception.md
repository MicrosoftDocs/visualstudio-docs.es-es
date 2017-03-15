---
title: "Soluci&#243;n de problemas de excepciones: System.DuplicateWaitObjectException | Microsoft Docs"
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
  - "DuplicateWaitObjectException (clase)"
ms.assetid: b9ff6932-a7cf-4a89-bd7d-e4ef1a3ff353
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.DuplicateWaitObjectException
Si la matriz de los objetos <xref:System.DuplicateWaitObjectException> pasados a <xref:System.Threading.WaitHandle> u <xref:System.Threading.WaitHandle.WaitAll%2A> contiene cualquier identificador del sistema operativo duplicado, se produce una excepción <xref:System.Threading.WaitHandle.WaitAny%2A>.  
  
## Sugerencias asociadas  
 **Asegúrese de que los objetos WaitHandle que se pasan a WaitAll o WaitAny son únicos.**  
 Una matriz <xref:System.Threading.WaitHandle> no puede contener varias referencias al mismo objeto.  
  
### Comentarios  
 Common Language Runtime \(CLR\) proporciona un mecanismo de sincronización de subprocesos basado en objetos de sincronización que esperan la ejecución en una matriz de objetos <xref:System.Threading.WaitHandle>.  
  
## Vea también  
 <xref:System.DuplicateWaitObjectException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)