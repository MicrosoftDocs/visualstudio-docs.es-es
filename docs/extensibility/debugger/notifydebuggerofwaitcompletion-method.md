---
title: NotifyDebuggerOfWaitCompletion (método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679546"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion (método)
Método de marcador de posición usado como un destino de punto de interrupción por el depurador. Este método no debe ser entre líneas u optimizado.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Comentarios
 Todas las operaciones de combinación con una tarea deben llamar a este método si se establece su bit de notificación del depurador.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)