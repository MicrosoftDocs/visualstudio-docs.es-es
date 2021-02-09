---
title: 'IDebugProcess3:: Continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ac7109b9f92a4ed7eecf57095c44fc4208b9f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891064"
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

## <a name="remarks"></a>Notas
 Este método se llama en este proceso, independientemente del número de procesos que se están depurando o del proceso que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar con la ejecución como si nunca se hubiera detenido antes de completar su ejecución anterior. Es decir, si un subproceso de este proceso estaba realizando una operación de paso a través y se detuvo porque se detuvo algún otro proceso y, a continuación, `Continue` se llamó a, el subproceso especificado debe completar la operación de paso a través original.

 **ADVERTENCIA** de No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
