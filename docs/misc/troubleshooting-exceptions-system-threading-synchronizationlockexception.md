---
title: "Soluci&#243;n de problemas de excepciones: System.Threading.SynchronizationLockException | Microsoft Docs"
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
  - "SynchronizationLockException (excepción)"
  - "System.Threading.SynchronizationLockException (excepción)"
ms.assetid: 82d80643-fc5c-40ae-a579-46869772d25c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Threading.SynchronizationLockException
La excepción que se produce cuando un método requiere que el llamante sea propietario del bloqueo en un `Monitor` determinado, y que el método lo invoque un llamante que no sea propietario de dicho bloqueo.  
  
## Comentarios  
 Se produce una excepción <xref:System.Threading.SynchronizationLockException> al llamar a los métodos <xref:System.Threading.Monitor.Exit%2A>, <xref:System.Threading.Monitor.Pulse%2A>, <xref:System.Threading.Monitor.PulseAll%2A>, y <xref:System.Threading.Monitor.Wait%2A> de la clase `Monitor` desde un bloque de código no sincronizado.  
  
## Vea también  
 <xref:System.Threading.SynchronizationLockException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)