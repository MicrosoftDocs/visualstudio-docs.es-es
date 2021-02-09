---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 544ca22d263a3fca47f9484ac126031e83cde4e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911905"
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

## <a name="remarks"></a>Notas
 En caso de que haya cualquier sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos del programa deben ejecutarse cuando un subproceso determinado se está ejecutando.

> [!WARNING]
> No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
