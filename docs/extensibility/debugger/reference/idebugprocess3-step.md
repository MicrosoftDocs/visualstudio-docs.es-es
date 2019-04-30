---
title: IDebugProcess3::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 296c76a386b72c3435a90e207dd76f9eeca56422
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412952"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Hace que el proceso paso a paso una instrucción o instrucción.

> [!NOTE]
> Este método debería usarse en lugar de [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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

#### <a name="parameters"></a>Parámetros
 `pThread`

 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso que se va a escalonado.

 `sk`

 [in] Uno de los [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valores.

 `step`

 [in] Uno de los [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valores.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve el código de error.

## <a name="remarks"></a>Comentarios
 En caso de que no hay ninguna sincronización de subprocesos o la comunicación entre subprocesos, otros subprocesos del proceso deben ejecutarse cuando un subproceso en particular es ejecución paso a paso.

 **Advertencia** no enviar ningún evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.

## <a name="see-also"></a>Vea también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)