---
title: "GetScheduledTasksForDebugger (m&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Método GetScheduledTasksForDebugger, clase de TaskScheduler [motores de depuración de .NET Framework]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetScheduledTasksForDebugger (m&#233;todo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una matriz de todas las tareas programadas.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## Valor devuelto  
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.  
  
## Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> debe llamarse desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.  
  
## Vea también  
 [TaskScheduler \(clase\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)