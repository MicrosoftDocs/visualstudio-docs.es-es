---
description: Sigue ejecutando este proceso desde un estado detenido. Se conserva cualquier estado de ejecución anterior (como un paso) y el proceso empieza a ejecutarse de nuevo.
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11f2d5b652b950976834b8ba18f71a1dc0d1b34c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081586"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Sigue ejecutando este proceso desde un estado detenido. Se conserva cualquier estado de ejecución anterior (como un paso) y el proceso empieza a ejecutarse de nuevo.

> [!NOTE]
> Este método se debe usar en lugar de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
de Objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso que se va a continuar.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 Este método se llama en este proceso, independientemente del número de procesos que se están depurando o del proceso que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar con la ejecución como si nunca se hubiera detenido antes de completar su ejecución anterior. Es decir, si un subproceso de este proceso estaba realizando una operación de paso a través y se detuvo porque se detuvo algún otro proceso y, a continuación, `Continue` se llamó a, el subproceso especificado debe completar la operación de paso a través original.

 **ADVERTENCIA** de No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Consulte también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
