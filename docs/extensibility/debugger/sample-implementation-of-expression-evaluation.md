---
title: Ejemplo de implementación de evaluación de expresiones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0135c8dd61ca2505c1458bc157b574e6bcbee09a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315068"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ejemplo de implementación de evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [administrado evaluador ejemplo](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Para un **inspección** expresión de la ventana, las llamadas de Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para generar un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. `IDebugExpressionContext2::ParseText` crea una instancia de un evaluador de expresiones (EE) y llama a [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

 El `IDebugExpressionEvaluator::Parse` realiza las siguientes tareas:

1. [C++ sólo] Analiza la expresión para buscar errores.

2. Crea una instancia de una clase (llamado `CParsedExpression` en este ejemplo) que se ejecuta el `IDebugParsedExpression` interfaz y almacena en la clase se puede analizar la expresión.

3. Devuelve el `IDebugParsedExpression` interfaz desde el `CParsedExpression` objeto.

> [!NOTE]
> En los ejemplos siguientes y en el ejemplo MyCEE, el evaluador de expresiones no separa el análisis de la evaluación.

## <a name="managed-code"></a>Código administrado
 El código siguiente muestra una implementación de `IDebugExpressionEvaluator::Parse` en código administrado. Esta versión del método aplaza el análisis a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) como el código para el análisis también se evalúa al mismo tiempo (consulte [evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código no administrado
El código siguiente es una implementación de `IDebugExpressionEvaluator::Parse` en código no administrado. Este método llama a una función auxiliar, `Parse`, para analizar la expresión y compruebe si hay errores, pero este método omite el valor resultante. La evaluación formal se aplaza hasta [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) donde se puede analizar la expresión mientras se evalúa (consulte [evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)