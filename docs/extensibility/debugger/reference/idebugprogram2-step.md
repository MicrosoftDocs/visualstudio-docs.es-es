---
description: Realiza un paso.
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2470c62215c8c708056f7c123adc5eac3a5e389d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084498"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Realiza un paso.

> [!NOTE]
> Este método es desusado. En su lugar, use el método [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

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
de Un objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso escalonado.

`sk`\
de Un valor de la enumeración [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) que especifica el tipo de paso.

`step`\
de Un valor de la enumeración [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) que especifica la unidad de paso (por ejemplo, por instrucción o instrucción).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 En caso de que haya cualquier sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos del programa deben ejecutarse cuando un subproceso determinado se está ejecutando.

> [!WARNING]
> No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
