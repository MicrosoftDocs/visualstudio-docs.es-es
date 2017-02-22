---
title: "Campo TASK_STATE_CANCELED | Microsoft Docs"
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
  - "Campo TASK_STATE_CANCELED, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Campo TASK_STATE_CANCELED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tarea se canceló antes de que ha alcanzado el estado de ejecución, o se confirma su cancelación y completa sin excepciones.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## Comentarios  
 Si el [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene este valor, el <xref:System.Threading.Tasks.Task.Status%2A> devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)