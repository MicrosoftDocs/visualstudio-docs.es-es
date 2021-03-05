---
description: Hace que el proceso procese una instrucción o instrucción.
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85df970c073fa2203873733073c5b6b85cabe06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150138"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Hace que el proceso procese una instrucción o instrucción.

> [!NOTE]
> Este método se debe usar en lugar del [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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
de Un objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso escalonado.

`sk`\
de Uno de los valores de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
de Uno de los valores de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve el código de error.

## <a name="remarks"></a>Observaciones
 En caso de que haya cualquier sincronización de subprocesos o comunicación entre subprocesos, otros subprocesos del proceso deben ejecutarse cuando un subproceso determinado se está ejecutando.

 **ADVERTENCIA** de No enviar un evento de detención o un evento inmediato (sincrónico) al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; de lo contrario, es posible que el depurador deje de responder.

## <a name="see-also"></a>Consulte también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
