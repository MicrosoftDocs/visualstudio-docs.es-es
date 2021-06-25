---
title: Método NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Obtenga información sobre el método NotifyDebuggerOfWaitCompletion, que es un marcador de posición utilizado como destino de punto de interrupción por el depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9d6b5fbdcb8195709a751117056bcaa0617eff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904222"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Método NotifyDebuggerOfWaitCompletion
Método de marcador de posición utilizado como destino de punto de interrupción por el depurador. Este método no se debe incluir ni optimizar.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Observaciones
 Todas las operaciones de combinación con una tarea deben llamar a este método si se establece el bit de notificación del depurador.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
