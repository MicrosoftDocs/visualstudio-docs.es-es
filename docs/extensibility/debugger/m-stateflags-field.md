---
title: m_stateFlags campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6e49ad2965ef99d5ceaafc3cb5f4de3589321d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925239"
---
# <a name="m_stateflags-field"></a>m_stateFlags campo
Almacena información sobre el estado actual del <xref:System.Threading.Tasks.Task> objeto.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Observaciones
 Normalmente, se utiliza la <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> propiedad para tener acceso a este valor.

 Este miembro puede ser cualquier combinación de los siguientes valores:

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
