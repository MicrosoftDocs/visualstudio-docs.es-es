---
title: Implementación de GetMethodProperty | Microsoft Docs
description: Aprenda cómo Visual Studio obtiene información sobre el método actual en el marco de pila mediante el Getdebugproperty (del motor de depuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6028bd92611e7d5dc8a7e05fcf98bc360de7e9ed
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559919"
---
# <a name="implement-getmethodproperty"></a>Implementación de GetMethodProperty
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio llama a la (DE) [getdebugproperty (](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)del motor de depuración, que a su vez llama a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener información sobre el método actual en el marco de pila.

Esta implementación de `IDebugExpressionEvaluator::GetMethodProperty` realiza las siguientes tareas:

1. Llama a [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), pasando el objeto [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) . El proveedor de símbolos (SP) devuelve un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.

2. Obtiene el [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) de `IDebugContainerField` .

3. Crea una instancia de una clase (a `CFieldProperty` la que se llama en este ejemplo) que implementa la interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) y contiene el `IDebugMethodField` objeto devuelto desde el SP.

4. Devuelve la `IDebugProperty2` interfaz del `CFieldProperty` objeto.

## <a name="managed-code"></a>Código administrado
En este ejemplo se muestra una implementación de `IDebugExpressionEvaluator::GetMethodProperty` en código administrado.

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
En este ejemplo se muestra una implementación de `IDebugExpressionEvaluator::GetMethodProperty` en código no administrado.

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
- [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)
