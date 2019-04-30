---
title: SetNotificationForWaitCompletion (método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 468850a441cfd0bc87155fd746d8578c6b763e66
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912931"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
Establece o borra el bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parámetros
 `enabled`

 `true` Para establecer el bit; `false` al anular el bit.

## <a name="exceptions"></a>Excepciones

## <a name="remarks"></a>Comentarios
 El depurador establece este bit para ayudar a paso fuera de un cuerpo de método asincrónico. Si `enabled` es `true`, este método debe llamarse únicamente en una tarea que no se ha completado todavía. Cuando `enabled` es `false`, este método puede llamarse en las tareas completadas. En cualquier caso, solo debe usarse para tareas de la promesa de estilo.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)