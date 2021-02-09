---
title: Método GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 318e535d86dcd51f9c9bbfcfae8e228c8d7c20b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921340"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (Método)
Recupera una matriz de todas las tareas programadas.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valor devuelto
 Una matriz de todas las tareas programadas. Cada tarea se está ejecutando o ha terminado de ejecutarse.

## <a name="remarks"></a>Notas
 Este método no es seguro para subprocesos y no se debe utilizar simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> . Llame a este método desde un depurador solo cuando el depurador haya suspendido todos los demás subprocesos.

## <a name="see-also"></a>Vea también
- [TaskScheduler (clase)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
