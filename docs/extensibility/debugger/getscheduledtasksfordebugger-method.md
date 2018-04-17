---
title: Método GetScheduledTasksForDebugger | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 20cde88083acd38df780468927faec5fbd142b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (método)
Recupera una matriz de todas las tareas programadas.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> debe llamarse desde un depurador solo cuando el depurador suspende todos los demás subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Clase de objeto TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)