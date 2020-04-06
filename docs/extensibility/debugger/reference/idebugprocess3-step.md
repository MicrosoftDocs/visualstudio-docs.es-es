---
title: IDebugProcess3::Paso ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723553"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Hace que el proceso realice un paso de una instrucción o instrucción.

> [!NOTE]
> Este método debe utilizarse en lugar de [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
[en] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se va a escalonar.

`sk`\
[en] Uno de los valores [STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[en] Uno de los valores [STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario devuelve código de error.

## <a name="remarks"></a>Observaciones
 En caso de que haya alguna sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos en el proceso deben ejecutarse cuando un subproceso determinado está paso a paso.

 **Advertencia** No envíe un evento de detención o un evento inmediato (sincrónico) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; de lo contrario, el depurador puede bloquearse.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
