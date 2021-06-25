---
title: Obtener propiedades locales | Microsoft Docs
description: Obtenga información Visual Studio usa EnumChildren para obtener propiedades locales con estos ejemplos para código administrado y no administrado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c45933c6340836fac889f1309c14a71feed31791
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900738"
---
# <a name="get-local-properties"></a>Obtener propiedades locales
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de [evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio llama [a EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un objeto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que proporciona acceso a todas las opciones locales que se mostrarán en la **ventana Locales.** Visual Studio a continuación, llama a [Siguiente](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener la información que se va a mostrar para cada local. En este ejemplo, la clase `CEnumPropertyInfo` implementa la `IEnumDebugPropertyInfo2` interfaz .

Esta implementación de `IEnumDebugPropertyInfo2::Next` realiza las siguientes tareas:

1. Borra la matriz donde se va a almacenar la información.

2. Llama [a Next](../../extensibility/debugger/reference/ienumdebugfields-next.md) para cada local, almacenando el DEBUG_PROPERTY_INFO devuelto en la matriz que se va a devolver. [](../../extensibility/debugger/reference/debug-property-info.md) El [objeto IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) se proporcionó cuando se hubo una instancia de `CEnumPropertyInfo` esta clase.

## <a name="managed-code"></a>Código administrado
En este ejemplo se muestra una implementación de para las locales de un método `IEnumDebugPropertyInfo2::EnumChildren` en código administrado.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código no administrado
 En este ejemplo se muestra una implementación de para las locales de un método `IEnumDebugPropertyInfo2::EnumChildren` en código no administrado.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Consulta también
- [Implementación de ejemplo de locales](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Enumeración de las locales](../../extensibility/debugger/enumerating-locals.md)
