---
title: SetNotificationForWaitCompletion (Método) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712872"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
Establece o borra el bit de estado de TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parámetros
 `enabled`

 `true`para establecer el bit; `false` para desajustar el bit.

## <a name="exceptions"></a>Excepciones

## <a name="remarks"></a>Observaciones
 El depurador establece este bit para ayudar a salir de un cuerpo de método asincrónico. Si `enabled` `true`es , se debe llamar a este método solo en una tarea que aún no se ha completado. Cuando `enabled` `false`es , se puede llamar a este método en las tareas completadas. En cualquier caso, solo se debe usar para tareas de estilo de promesa.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
