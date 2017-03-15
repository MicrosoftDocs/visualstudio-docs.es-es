---
title: "Campo TASK_STATE_EXECUTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Campo TASK_STATE_EXECUTED, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Campo TASK_STATE_EXECUTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tarea se está ejecutando pero aún no se ha completado.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## Comentarios  
 Si el [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene este valor, el <xref:System.Threading.Tasks.Task.Status%2A> devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)