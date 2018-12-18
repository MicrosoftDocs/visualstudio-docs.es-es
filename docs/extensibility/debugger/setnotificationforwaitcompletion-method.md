---
title: SetNotificationForWaitCompletion (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42c5bca56bc46c0b8124fbfaf7ca046c2c1e59ec
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276343"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (Método)
Establece o borra el bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
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
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)