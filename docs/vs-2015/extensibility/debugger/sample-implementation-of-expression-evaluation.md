---
title: Implementación de ejemplo de evaluación de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7a19247b296d7e00a15051e75dd53536133c426
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147243"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementación de ejemplo de la evaluación de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 En el caso de una expresión de ventana de **inspección** , Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para generar un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` crea una instancia del evaluador de expresiones (EE) y llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener un objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
 Esta implementación de `IDebugExpressionEvaluator::Parse` realiza las siguientes tareas:  
  
1. [Solo C++] Analiza la expresión para buscar errores.  
  
2. Crea una instancia de una clase (a `CParsedExpression` la que se llama en este ejemplo) que implementa la `IDebugParsedExpression` interfaz y almacena en la clase la expresión que se va a analizar.  
  
3. Devuelve la `IDebugParsedExpression` interfaz del `CParsedExpression` objeto.  
  
> [!NOTE]
> En los ejemplos siguientes y en el ejemplo MyCEE, el evaluador de expresiones no separa el análisis de la evaluación.  
  
## <a name="managed-code"></a>Código administrado  
 Se trata de una implementación de `IDebugExpressionEvaluator::Parse` en código administrado. Tenga en cuenta que esta versión del método pospone el análisis a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , ya que el código para el análisis también se evalúa al mismo tiempo (vea [evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
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
 Se trata de una implementación de `IDebugExpressionEvaluator::Parse` en código no administrado. Este método llama a una función auxiliar, `Parse` , para analizar la expresión y comprobar si hay errores, pero este método omite el valor resultante. La evaluación formal se difiere en [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) donde se analiza la expresión mientras se evalúa (consulte [evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
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
  
## <a name="see-also"></a>Consulte también  
 [Evaluación de una expresión de ventana de inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)
