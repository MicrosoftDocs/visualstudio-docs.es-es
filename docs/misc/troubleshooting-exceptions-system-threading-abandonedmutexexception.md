---
title: "Soluci&#243;n de problemas de excepciones: System.Threading.AbandonedMutexException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Threading.AbandonedMutexException (excepción)"
  - "AbandonedMutexException (excepción)"
ms.assetid: 11157066-32ed-492c-83af-29983f915eec
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Threading.AbandonedMutexException
La excepción que se produce cuando un subproceso está esperando un objeto Mutex, y otro subproceso abandona el Mutex saliendo sin liberarlo.  
  
## Comentarios  
 Por lo general, un Mutex abandonado indica un error grave en el código. Cuando un subproceso sale sin liberar el Mutex, puede que las estructuras de datos protegidas por el Mutex no estén en un estado coherente. El siguiente subproceso que solicite la propiedad del Mutex podrá controlar esta excepción y continuar si se puede comprobar la integridad de las estructuras de datos.  
  
## Vea también  
 <xref:System.Threading.AbandonedMutexException>   
 <xref:System.Threading.Mutex>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Subprocesos](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)