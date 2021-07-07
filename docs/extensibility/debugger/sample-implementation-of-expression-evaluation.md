---
title: Implementación de ejemplo de la evaluación de expresiones | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio llama a ParseText a fin de generar un objeto IDebugExpression2 para una expresión de la ventana Inspección.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902311"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementación de ejemplo de la evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea [Evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Para una expresión de la ventana **Inspección**, Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a fin de generar un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md). `IDebugExpressionContext2::ParseText` crea una instancia de un evaluador de expresiones (EE) y llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md).

 `IDebugExpressionEvaluator::Parse` realiza las tareas siguientes:

1. [Solo C++] Analiza la expresión para buscar errores.

2. Crea una instancia de una clase (denominada `CParsedExpression` en este ejemplo) que ejecuta la interfaz `IDebugParsedExpression` y almacena en la clase la expresión que se va a analizar.

3. Devuelve la interfaz `IDebugParsedExpression` desde el objeto `CParsedExpression`.

> [!NOTE]
> En los ejemplos siguientes y en el de MyCEE, el evaluador de expresiones no separa el análisis de la evaluación.

## <a name="managed-code"></a>Código administrado
 En el código siguiente se muestra una implementación de `IDebugExpressionEvaluator::Parse` en código administrado. Esta versión del método difiere el análisis a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md), ya que el código para analizar también se evalúa al mismo tiempo (vea [Evaluación de una expresión de Inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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
El código siguiente es una implementación de `IDebugExpressionEvaluator::Parse` en código no administrado. Este método llama a una función auxiliar, `Parse`, para analizar la expresión y comprobar si hay errores, pero este método omite el valor resultante. La evaluación formal se difiere a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md), donde se analiza la expresión mientras se evalúa (vea [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).

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

## <a name="see-also"></a>Consulta también
- [Evaluación de una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)
