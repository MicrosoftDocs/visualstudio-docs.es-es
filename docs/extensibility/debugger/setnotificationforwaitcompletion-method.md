---
title: Método SetNotificationForWaitCompletion | Microsoft Docs
description: Obtenga información sobre cómo el depurador usa un bit de estado para ayudar a salir de un cuerpo de método asincrónico para las tareas de estilo de promesa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ec469ed4f9c4fa2e503b2350235299a81a94bf9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902116"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
Establece o borra el TASK_STATE_WAIT_COMPLETION_NOTIFICATION de estado.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parámetros
 `enabled`

 `true` para establecer el bit; `false` para desaconjunto el bit.

## <a name="exceptions"></a>Excepciones

## <a name="remarks"></a>Notas
 El depurador establece este bit para ayudar a salir de un cuerpo de método asincrónico. Si `enabled` es , solo se debe llamar a este método en una tarea que aún no se haya `true` completado. Cuando `enabled` es , se puede llamar a este método en tareas `false` completadas. En cualquier caso, solo se debe usar para tareas de estilo de promesa.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
