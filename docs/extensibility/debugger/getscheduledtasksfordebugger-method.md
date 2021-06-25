---
description: Recupera una matriz de todas las tareas programadas.
title: Método GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 51da481edb636450770d0cff569b9ef411e17cf6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900959"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (Método)
Recupera una matriz de todas las tareas programadas.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a este miembro interno desde la .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.

## <a name="remarks"></a>Observaciones
 Este método no es seguro para subprocesos y no debe usarlo simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> . Llame a este método desde un depurador solo cuando el depurador haya suspendido todos los demás subprocesos.

## <a name="see-also"></a>Consulta también
- [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
