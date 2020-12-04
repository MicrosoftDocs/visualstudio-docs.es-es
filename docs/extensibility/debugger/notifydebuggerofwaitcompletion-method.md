---
title: Método NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: Obtenga información sobre el método NotifyDebuggerOfWaitCompletion, que es un marcador de posición que el depurador usa como destino de punto de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606637"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Método NotifyDebuggerOfWaitCompletion
Método de marcador de posición utilizado como destino de punto de interrupción por el depurador. Este método no debe estar alineado ni optimizado.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Sintaxis

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Comentarios
 Todas las operaciones de combinación con una tarea deben llamar a este método si se establece el bit de notificación del depurador.

## <a name="requirements"></a>Requisitos

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
