---
title: Implementación de ejemplo de evaluación de expresiones | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio llama a ParseText para generar un objeto IDebugExpression2 para una expresión de inspección de ventanas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec7ddd5270fdac3513c3f63673e5a5f3d05464b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960954"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementación de ejemplo de evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 En el caso de una expresión de ventana de **inspección** , Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para generar un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` crea una instancia del evaluador de expresiones (EE) y llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

 `IDebugExpressionEvaluator::Parse`Realiza las tareas siguientes:

1. [Solo C++] Analiza la expresión para buscar errores.

2. Crea una instancia de una clase (a `CParsedExpression` la que se llama en este ejemplo) que ejecuta la `IDebugParsedExpression` interfaz y almacena en la clase la expresión que se va a analizar.

3. Devuelve la `IDebugParsedExpression` interfaz del `CParsedExpression` objeto.

> [!NOTE]
> En los ejemplos siguientes y en el ejemplo MyCEE, el evaluador de expresiones no separa el análisis de la evaluación.

## <a name="managed-code"></a>Código administrado
 En el código siguiente se muestra una implementación de `IDebugExpressionEvaluator::Parse` en código administrado. Esta versión del método pospone el análisis a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , ya que el código para el análisis también se evalúa al mismo tiempo (vea [evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
El código siguiente es una implementación de `IDebugExpressionEvaluator::Parse` en código no administrado. Este método llama a una función auxiliar, `Parse` , para analizar la expresión y comprobar si hay errores, pero este método omite el valor resultante. La evaluación formal se difiere en [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) donde se analiza la expresión mientras se evalúa (vea [evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
- [Evaluar una expresión de ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)
