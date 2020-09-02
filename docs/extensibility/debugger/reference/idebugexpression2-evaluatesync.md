---
title: 'IDebugExpression2:: EvaluateSync | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controla la evaluación de expresiones.

`dwTimeout`\
de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

`pExprCallback`\
de Este parámetro siempre es un valor null.

`ppResult`\
enuncia Devuelve el objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que contiene el resultado de la evaluación de la expresión.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error. Algunos códigos de error típicos son:

|Error|Descripción|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Otra expresión se está evaluando actualmente y no se admite la evaluación de expresiones simultáneas.|
|E_EVALUATE_TIMEOUT|Se agotó el tiempo de espera de la evaluación.|

## <a name="remarks"></a>Observaciones
En el caso de la evaluación sincrónica, no es necesario volver a enviar un evento a Visual Studio cuando se completa la evaluación.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CExpression` objeto simple que implementa la interfaz [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) .

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
