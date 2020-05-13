---
title: IDebugExpression2::EvaluateSync ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729676"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Este método evalúa la expresión sincrónicamente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parámetros
`dwFlags`\
[en] Combinación de indicadores de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controlan la evaluación de expresiones.

`dwTimeout`\
[en] Tiempo máximo, en milisegundos, para esperar antes de volver de este método. Se `INFINITE` usa para esperar indefinidamente.

`pExprCallback`\
[en] Este parámetro siempre es un valor nulo.

`ppResult`\
[fuera] Devuelve el objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que contiene el resultado de la evaluación de expresiones.

## <a name="return-value"></a>Valor devuelto
Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error. Algunos códigos de error típicos son:

|Error|Descripción|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Actualmente se está evaluando otra expresión y no se admite la evaluación simultánea de expresiones.|
|E_EVALUATE_TIMEOUT|Evaluación agotada.|

## <a name="remarks"></a>Observaciones
Para la evaluación sincrónica, no es necesario devolver un evento a Visual Studio al finalizar la evaluación.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CExpression` cómo implementar este método para un objeto simple que implementa el [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaz.

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
