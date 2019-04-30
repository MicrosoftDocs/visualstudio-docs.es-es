---
title: IDebugExpression2::Abort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 490c131820cbe16b8e18be649ad5439c024ad3c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874249"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Este método cancela la evaluación de expresiones asincrónica como iniciado mediante una llamada a la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cuando se ha cancelado la evaluación de expresiones asincrónicas, no envía una [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) eventos a la devolución de llamada de evento que se pasan a la [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos.

## <a name="see-also"></a>Vea también
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)