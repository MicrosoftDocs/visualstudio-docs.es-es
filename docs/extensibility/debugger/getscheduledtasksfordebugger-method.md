---
title: GetScheduledTasksForDebugger (método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 221a1b49bd3083e0d2dd0248cdf182d699423057
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695887"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (Método)
Recupera una matriz de todas las tareas programadas.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.

## <a name="remarks"></a>Comentarios
 Este método no es seguro para subprocesos y no debe usar simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Llame a este método desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.

## <a name="see-also"></a>Vea también
- [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)