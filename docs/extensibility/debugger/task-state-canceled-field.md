---
description: La tarea se canceló antes de alcanzar el estado en ejecución o confirmó su cancelación y se completó sin excepción.
title: TASK_STATE_CANCELED campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90b3c048edb4e52a426a2fd40d8bfd31168fea7d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900179"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
La tarea se canceló antes de alcanzar el estado en ejecución o confirmó su cancelación y se completó sin excepción.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede acceder a este miembro interno desde la .NET Framework, se proporciona la siguiente sintaxis en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Observaciones
 Si el [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene este valor, la <xref:System.Threading.Tasks.Task.Status%2A> propiedad devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Consulta también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
