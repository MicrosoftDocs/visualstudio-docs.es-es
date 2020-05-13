---
title: IDebugProcess3::Continuar á Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723769"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continúa ejecutando este proceso desde un estado detenido. Se conserva cualquier estado de ejecución anterior (por ejemplo, un paso) y el proceso comienza a ejecutarse de nuevo.

> [!NOTE]
> Este método debe utilizarse en lugar de [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Continue(
   IDebugThread2* pThread
);
```

```csharp
int Continue(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se va a continuar.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método en este proceso independientemente de cuántos procesos se están depurando o qué proceso generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar la ejecución como si nunca se hubiera detenido antes de completar su ejecución anterior. Es decir, si un subproceso de este proceso realizaba una operación de paso `Continue` a paso y se detuvo porque se detuvo algún otro proceso y, a continuación, se llamó, el subproceso especificado debe completar la operación de paso a paso original.

 **Advertencia** No envíe un evento de detención o un evento inmediato (sincrónico) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; de lo contrario, el depurador puede bloquearse.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
