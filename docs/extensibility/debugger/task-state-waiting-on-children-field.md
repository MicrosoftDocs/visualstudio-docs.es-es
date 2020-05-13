---
title: Campo de TASK_STATE_WAITING_ON_CHILDREN Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712582"
---
# <a name="task_state_waiting_on_children-field"></a>campo TASK_STATE_WAITING_ON_CHILDREN
La tarea ha terminado de ejecutar su delegado y está esperando implícitamente a que se completen las tareas secundarias adjuntas.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede tener acceso a este miembro interno desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Observaciones
 Si el campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene <xref:System.Threading.Tasks.Task.Status%2A> este <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>valor, la propiedad devuelve .

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
