---
title: Evaluar una expresión de inspección | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio usa EvaluateSync cuando está listo para mostrar el valor de una expresión de inspección.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 84e3b020da8d7fc6e4d7f3be89eaa50cd59c704e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851340"
---
# <a name="evaluate-a-watch-expression"></a>Evaluación de una expresión de inspección
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Cuando Visual Studio está listo para mostrar el valor de una expresión de inspección, llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), que a su vez llama a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Este proceso genera un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que contiene el valor y el tipo de la expresión.

En esta implementación de `IDebugParsedExpression::EvaluateSync` , la expresión se analiza y se evalúa al mismo tiempo. Esta implementación realiza las siguientes tareas:

1. Analiza y evalúa la expresión para generar un objeto genérico que contiene el valor y su tipo. En C#, esto se representa como un `object` tiempo en C++, que se representa como `VARIANT` .

2. Crea una instancia de una clase (a la `CValueProperty` que se llama en este ejemplo) que implementa la `IDebugProperty2` interfaz y almacena en la clase el valor que se va a devolver.

3. Devuelve la `IDebugProperty2` interfaz del `CValueProperty` objeto.

## <a name="managed-code"></a>Código administrado
Se trata de una implementación de `IDebugParsedExpression::EvaluateSync` en código administrado. El método auxiliar `Tokenize` analiza la expresión en un árbol de análisis. La función auxiliar `EvalToken` convierte el token en un valor. La función auxiliar `FindTerm` atraviesa de forma recursiva el árbol de análisis, llamando a `EvalToken` para cada nodo que representa un valor y aplicando las operaciones (suma o resta) en la expresión.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código no administrado
Se trata de una implementación de `IDebugParsedExpression::EvaluateSync` en código no administrado. La función auxiliar `Evaluate` analiza y evalúa la expresión, y devuelve un `VARIANT` que contiene el valor resultante. La función auxiliar `VariantValueToProperty` agrupa el `VARIANT` en un `CValueProperty` objeto.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Vea también
- [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Implementación de ejemplo de evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
