---
title: "Campo TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs"
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
  - "Campo TASK_STATE_RAN_TO_COMPLETION, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Campo TASK_STATE_RAN_TO_COMPLETION
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tarea terminó de ejecutarse correctamente.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## Comentarios  
 Si el [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene este valor, el <xref:System.Threading.Tasks.Task.Status%2A> devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)