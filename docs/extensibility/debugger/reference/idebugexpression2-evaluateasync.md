---
title: IDebugExpression2::EvaluateAsync ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729754"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Este método evalúa la expresión de forma asincrónica.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parámetros
`dwFlags`\
[en] Combinación de indicadores de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controlan la evaluación de expresiones.

`pExprCallback`\
[en] Este parámetro siempre es un valor nulo.

## <a name="return-value"></a>Valor devuelto
Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error. Un código de error típico es:

|Error|Descripción|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Actualmente se está evaluando otra expresión y no se admite la evaluación simultánea de expresiones.|

## <a name="remarks"></a>Observaciones
Este método debe devolver inmediatamente después de que haya iniciado la evaluación de expresiones. Cuando la expresión se evalúa correctamente, un [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) debe enviarse a la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) devolución de llamada de eventos como se proporciona a través [de Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CExpression` cómo implementar este método para un objeto simple que implementa el [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaz.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Vea también
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
