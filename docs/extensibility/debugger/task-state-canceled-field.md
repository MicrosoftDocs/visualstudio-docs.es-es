---
title: Campo de TASK_STATE_CANCELED de la TASK_STATE_CANCELED Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712753"
---
# <a name="task_state_canceled-field"></a>campo TASK_STATE_CANCELED
La tarea se canceló antes de que alcanzara el estado de ejecución o confirmó su cancelación y se completó sin excepción.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede tener acceso a este miembro interno desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Observaciones
 Si el campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene <xref:System.Threading.Tasks.Task.Status%2A> este <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>valor, la propiedad devuelve .

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
