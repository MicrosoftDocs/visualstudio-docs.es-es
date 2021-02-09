---
title: 'IDebugExpression2:: EvaluateAsync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8af09c2db00b1f24631418c5332811cf4cb9202c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916263"
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
de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controla la evaluación de expresiones.

`pExprCallback`\
de Este parámetro siempre es un valor null.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Un código de error típico es:

|Error|Descripción|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Otra expresión se está evaluando actualmente y no se admite la evaluación de expresiones simultáneas.|

## <a name="remarks"></a>Notas
Este método debe volver inmediatamente después de que se haya iniciado la evaluación de la expresión. Cuando la expresión se evalúa correctamente, se debe enviar una [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a la devolución de llamada del evento [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) como se proporciona mediante [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CExpression` objeto simple que implementa la interfaz [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .

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
