---
title: "Campo TASK_STATE_WAITING_ON_CHILDREN | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_WAITING_ON_CHILDREN, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Campo TASK_STATE_WAITING_ON_CHILDREN
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tarea ha terminado de ejecutar a su delegado y está esperando implícitamente completar las tareas secundarias asociadas.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## Comentarios  
 Si el [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene este valor, el <xref:System.Threading.Tasks.Task.Status%2A> devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)