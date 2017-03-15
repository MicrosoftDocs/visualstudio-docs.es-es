---
title: "NotifyDebuggerOfWaitCompletion (m&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Método de NotifyDebuggerOfWaitCompletion, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# NotifyDebuggerOfWaitCompletion (m&#233;todo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Método de marcador de posición usado como un objetivo de punto de interrupción por el depurador. Este método no debe ser optimizado o entre líneas.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
## Sintaxis  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## Comentarios  
 Todas las operaciones de combinación con una tarea deben llamar a este método si se establece su bit de notificación del depurador.  
  
## Requisitos  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)