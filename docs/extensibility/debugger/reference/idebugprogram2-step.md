---
title: IDebugProgram2::Paso ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722762"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Realiza un paso.

> [!NOTE]
> Este método es desusado. Utilice el [método Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) en su lugar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se va a escalonar.

`sk`\
[en] Valor de la enumeración [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) que especifica el tipo de paso.

`step`\
[en] Valor de la enumeración [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) que especifica la unidad de paso (por ejemplo, mediante instrucción o instrucción).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En caso de que haya alguna sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos del programa deben ejecutarse cuando un subproceso determinado está paso a paso.

> [!WARNING]
> No envíe un evento de detención o un evento inmediato (sincrónico) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; de lo contrario, el depurador puede bloquearse.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
