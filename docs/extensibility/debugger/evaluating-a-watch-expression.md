---
title: "Evaluar una expresi&#243;n de inspecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "evaluación de expresiones, expresiones de inspección"
  - "expresiones de inspección"
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluar una expresi&#243;n de inspecci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando Visual Studio está listo para mostrar el valor de una expresión de inspección, llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) que llama a su vez [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Esto produce una [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que contiene el valor y el tipo de la expresión.  
  
 En esta implementación de `IDebugParsedExpression::EvaluateSync`, la expresión se analiza y se evalúa al mismo tiempo. Esta implementación realiza las siguientes tareas:  
  
1.  Analiza y evalúa la expresión para producir un objeto genérico que contiene el valor y su tipo. En C\#, esto se representa como un `object` mientras que en C\+\+ se representa como un `VARIANT`.  
  
2.  Crea una instancia de una clase \(denominada `CValueProperty` en este ejemplo\) que implementa el `IDebugProperty2` de interfaz y la almacena en la clase, el valor que se va a devolver.  
  
3.  Devuelve el `IDebugProperty2` de la interfaz de la `CValueProperty` objeto.  
  
## Código administrado  
 Se trata de una implementación de la `IDebugParsedExpression::EvaluateSync` en código administrado. El método auxiliar `Tokenize` analiza la expresión en un árbol de análisis. La función auxiliar `EvalToken` convierte el token en un valor. La función auxiliar `FindTerm` recorre de forma recursiva el árbol de análisis, una llamada a `EvalToken` para cada nodo que representa un valor y aplicar ninguna operación \(suma o resta\) en la expresión.  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT EvaluateSync( uint evalFlags, uint timeout, IDebugSymbolProvider provider, IDebugAddress address, IDebugBinder binder, string resultType, out IDebugProperty2 result) { HRESULT retval = COM.S_OK; this.evalFlags = evalFlags; this.timeout = timeout; this.provider = provider; this.address = address; this.binder = binder; this.resultType = resultType; try { IDebugField field = null; // Tokenize, then parse. tokens = Tokenize(expression); result = new CValueProperty( expression, (int) FindTerm(EvalToken(tokens[0], out field),1), field, binder); } catch (ParseException) { result = new CValueProperty(expression, "Huh?"); retval = COM.E_INVALIDARG; } return retval; } } }  
```  
  
## Código no administrado  
 Se trata de una implementación de la `IDebugParsedExpression::EvaluateSync` en código no administrado. La función auxiliar `Evaluate` analiza y evalúa la expresión que devuelve un `VARIANT` que contiene el valor resultante. La función auxiliar `VariantValueToProperty` agrupaciones el `VARIANT` en un `CValueProperty` objeto.  
  
```  
[C++] STDMETHODIMP CParsedExpression::EvaluateSync( in  DWORD                 evalFlags, in  DWORD                 dwTimeout, in  IDebugSymbolProvider* pprovider, in  IDebugAddress*        paddress, in  IDebugBinder*         pbinder, in  BSTR                  bstrResultType, out IDebugProperty2**     ppproperty ) { // dwTimeout parameter is ignored in this implementation. if (pprovider == NULL) return E_INVALIDARG; if (paddress == NULL) return E_INVALIDARG; if (pbinder == NULL) return E_INVALIDARG; if (ppproperty == NULL) return E_INVALIDARG; else *ppproperty = 0; HRESULT hr; VARIANT value; BSTR    bstrErrorMessage = NULL; hr = ::Evaluate( pprovider, paddress, pbinder, m_expr, &bstrErrorMessage, &value ); if (hr != S_OK) { if (bstrErrorMessage == NULL) return hr; //we can display better messages ourselves. HRESULT hrLocal = S_OK; VARIANT varType; VARIANT varErrorMessage; VariantInit( &varType ); VariantInit( &varErrorMessage ); varErrorMessage.vt      = VT_BSTR; varErrorMessage.bstrVal = bstrErrorMessage; CValueProperty* valueProperty = new CValueProperty(); if (valueProperty != NULL) { hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage); if (SUCCEEDED(hrLocal)) { hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2, reinterpret_cast<void**>(ppproperty) ); } } VariantClear(&varType); VariantClear(&varErrorMessage); //frees BSTR if (!valueProperty) return hr; valueProperty->Release(); if (FAILED(hrLocal)) return hr; } else { if (bstrErrorMessage != NULL) SysFreeString(bstrErrorMessage); hr = VariantValueToProperty( pprovider, paddress, pbinder, m_radix, m_expr, value, ppproperty ); VariantClear(&value); if (FAILED(hr)) return hr; } return S_OK; }  
```  
  
## Vea también  
 [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Ejemplo de implementación de evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)