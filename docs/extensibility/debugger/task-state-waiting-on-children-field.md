---
description: La tarea ha terminado de ejecutar su delegado y está esperando implícitamente a que se completen las tareas secundarias adjuntas.
title: TASK_STATE_WAITING_ON_CHILDREN campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b795a20ba19b1309b3f3bf972beed70549d72d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900166"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN campo
La tarea ha terminado de ejecutar su delegado y está esperando implícitamente a que se completen las tareas secundarias adjuntas.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a este miembro interno desde la .NET Framework, se proporciona la siguiente sintaxis en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Observaciones
 Si el [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene este valor, la <xref:System.Threading.Tasks.Task.Status%2A> propiedad devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Consulta también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
