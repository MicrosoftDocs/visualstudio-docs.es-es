---
title: Implementar GetMethodProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ed7207237a20e4dadc1284aca2d6b41a671353
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-getmethodproperty"></a>Implementar GetMethodProperty
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio llama el motor de depuración (Alemania) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), que a su vez, llama [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener información sobre el método actual en el marco de pila.  
  
 Esta implementación de `IDebugExpressionEvaluator::GetMethodProperty` realiza las tareas siguientes:  
  
1.  Llamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), pasando el [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) objeto. El proveedor de símbolos (SP) devuelve un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.  
  
2.  Obtiene el [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) desde el `IDebugContainerField`.  
  
3.  Crea una instancia de una clase (denominado `CFieldProperty` en este ejemplo) que implementa el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) de interfaz y contiene el `IDebugMethodField` objeto devuelto desde el SP.  
  
4.  Devuelve el `IDebugProperty2` interfaz desde el `CFieldProperty` objeto.  
  
## <a name="managed-code"></a>Código administrado  
 Este ejemplo muestra una implementación de `IDebugExpressionEvaluator::GetMethodProperty` en código administrado.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Código no administrado  
 Este ejemplo muestra una implementación de `IDebugExpressionEvaluator::GetMethodProperty` en código no administrado.  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)