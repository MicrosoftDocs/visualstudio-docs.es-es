---
title: TASK_STATE_CANCELED campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 76de853cfa1fbd524c87384da38a9438c6ac66bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883576"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
La tarea se canceló antes de alcanzar el estado de ejecución, o confirmó su cancelación y se completó sin excepción.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Observaciones
 Si el campo [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene este valor, la <xref:System.Threading.Tasks.Task.Status%2A> propiedad devuelve <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
