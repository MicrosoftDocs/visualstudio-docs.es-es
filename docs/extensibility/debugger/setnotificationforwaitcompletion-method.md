---
title: Método SetNotificationForWaitCompletion | Microsoft Docs
description: Obtenga información sobre cómo el depurador utiliza un bit de estado para ayudar a salir de un cuerpo de método asincrónico para las tareas de tipo Promise.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2418e958c027fea7fd39c93b0d5abbd95d64435b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960798"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
Establece o borra el bit de estado de TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parámetros
 `enabled`

 `true` para establecer el bit; `false` para anular el bit.

## <a name="exceptions"></a>Excepciones

## <a name="remarks"></a>Notas
 El depurador establece este bit para ayudar a salir de un cuerpo de método asincrónico. Si `enabled` es `true` , solo se debe llamar a este método en una tarea que aún no se ha completado. Cuando `enabled` es `false` , se puede llamar a este método en las tareas completadas. En cualquiera de los dos eventos, solo se debe usar para las tareas de tipo Promise.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
