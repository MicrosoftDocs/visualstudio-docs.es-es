---
title: Ejemplo de implementación de la evaluación de expresiones ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713096"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Ejemplo de implementación de la evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Para una expresión de ventana **De inspección,** Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para generar un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. `IDebugExpressionContext2::ParseText`crea una instancia de un evaluador de expresiones (EE) y llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

 Realiza `IDebugExpressionEvaluator::Parse` las siguientes tareas:

1. [Sólo C++] Analiza la expresión para buscar errores.

2. Crea una instancia `CParsedExpression` de una clase (llamada en este ejemplo) que ejecuta la `IDebugParsedExpression` interfaz y almacena en la clase la expresión que se va a analizar.

3. Devuelve `IDebugParsedExpression` la interfaz del `CParsedExpression` objeto.

> [!NOTE]
> En los ejemplos siguientes y en el ejemplo MyCEE, el evaluador de expresiones no separa el análisis de la evaluación.

## <a name="managed-code"></a>Código administrado
 El código siguiente muestra `IDebugExpressionEvaluator::Parse` una implementación de en código administrado. Esta versión del método aplaza el análisis a [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ya que el código para analizar también se evalúa al mismo tiempo (consulte [Evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
El código siguiente es `IDebugExpressionEvaluator::Parse` una implementación de código no administrado. Este método llama a `Parse`una función auxiliar, , para analizar la expresión y comprobar si hay errores, pero este método omite el valor resultante. La evaluación formal se aplaza a [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) donde se analiza la expresión mientras se evalúa (consulte [Evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Evaluar una expresión de ventana de inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Evaluar una expresión Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)
