---
title: Enumeración de locales ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 540c062d3d4f73a5468b39629fc277e6fd10df7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738870"
---
# <a name="enumerate-locals"></a>Enumerar locales
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Cuando Visual Studio está listo para rellenar el **locales** ventana, llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto desde [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) (consulte [implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren`devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto.

La `IDebugProperty2::EnumChildren` implementación realiza las siguientes tareas:

1. Garantiza que esto representa un método.

2. Utiliza `guidFilter` el argumento para determinar qué método llamar a la [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Si `guidFilter` es igual a:

    1. `guidFilterLocals`, llame a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) para obtener un objeto [IEnumDebugFields.](../../extensibility/debugger/reference/ienumdebugfields.md)

    2. `guidFilterArgs`, llame a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) para obtener un `IEnumDebugFields` objeto.

    3. `guidFilterLocalsPlusArgs`, sinteteten una `IDebugMethodField::EnumLocals` `IDebugMethodField::EnumArguments`enumeración que combine los resultados de y . Esta síntesis está `CEnumMethodField`representada por la clase .

3. Crea una instancia `CEnumPropertyInfo` de una clase (llamada `IEnumDebugPropertyInfo2` en este `IEnumDebugFields` ejemplo) que implementa la interfaz y contiene el objeto.

4. Devuelve `IEnumDebugProperty2Info2` la interfaz del `CEnumPropertyInfo` objeto.

## <a name="managed-code"></a>Código administrado
En este ejemplo `IDebugProperty2::EnumChildren` se muestra una implementación de en código administrado.

```csharp
namespace EEMC
{
    public class CFieldProperty : IDebugProperty2
    {
        public HRESULT EnumChildren (
                uint                    dwFields,
                uint                    radix,
            ref Guid                    guidFilter,
                ulong                   attribFilter,
                string                  nameFilter,
                uint                    timeout,
            out IEnumDebugPropertyInfo2 properties)
        {
            properties = null;
            IEnumDebugFields fields = null;

            // If this field is a method...
            if (0 != ((uint) fieldKind & (uint) FIELD_KIND.FIELD_TYPE_METHOD))
            {
                IDebugMethodField methodField = (IDebugMethodField) field;

                // Enumerate parameters.
                if (guidFilter == FilterGuids.guidFilterArgs)
                {
                    methodField.EnumParameters(out fields);
                }
                // Enumerate local variables.
                else if (guidFilter == FilterGuids.guidFilterLocals)
                {
                    methodField.EnumLocals(address, out fields);
                }
                // Enumerate all local variables, including invisible compiler temps.
                else if (guidFilter == FilterGuids.guidFilterAllLocals)
                {
                    methodField.EnumAllLocals(address, out fields);
                }
                // Enumerate "this", if any, and all parameters and local variables.
                else if (guidFilter == FilterGuids.guidFilterLocalsPlusArgs)
                {
                    IDebugClassField fieldThis  = null;
                    IEnumDebugFields parameters = null;
                    IEnumDebugFields locals     = null;

                    methodField.GetThis(out fieldThis);
                    methodField.EnumParameters(out parameters);
                    methodField.EnumLocals(address, out locals);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, parameters, locals);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                // Enumerate only "this".
                else if (guidFilter == FilterGuids.guidFilterThis)
                {
                    IDebugClassField fieldThis = null;
                    methodField.GetThis(out fieldThis);

                    CEnumMethodField enumMethodField =
                        new CEnumMethodField(fieldThis, null, null);
                    fields = (IEnumDebugFields) enumMethodField;
                }
                else throw new COMException();// E_FAIL
            }
            // Wrap a property enumerator around the field enumerator.
            CEnumPropertyInfo propertiesInfo =
                new CEnumPropertyInfo(provider, address, binder, radix, fields,
                (DEBUGPROP_INFO_FLAGS) dwFields);

            properties = (IEnumDebugPropertyInfo2) propertiesInfo;
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código no administrado
 En este ejemplo `IDebugProperty2::EnumChildren` se muestra una implementación de código no administrado.

```cpp
STDMETHODIMP CFieldProperty::EnumChildren(
        in DEBUGPROP_INFO_FLAGS        infoFlags,
        in DWORD                       radix,
        in REFGUID                     guidFilter,
        in DBG_ATTRIB_FLAGS            attribFilter,
        in LPCOLESTR                   pszNameFilter,
        in DWORD                       timeout,
        out IEnumDebugPropertyInfo2 ** ppchildren )
{
    if (ppchildren == NULL)
        return E_INVALIDARG;
    else
        *ppchildren = 0;

    //get enumeration
    HRESULT hr;
    IEnumDebugFields*     pfields    = NULL;

    if (m_fieldKind & FIELD_TYPE_METHOD)
    {
        //-----------------------------------------------------
        // A Method

        IDebugMethodField*  pmethod    = NULL;

        //enumerate the requested properties
        hr = m_field->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod) );
        if (FAILED(hr))
            return hr;

        if (guidFilter == guidFilterArgs)
        {
            hr = pmethod->EnumParameters( &pfields );
        }
        else if (guidFilter == guidFilterLocals)
        {
            hr = pmethod->EnumLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterAllLocals)
        {
            hr = pmethod->EnumAllLocals( m_address, &pfields );
        }
        else if (guidFilter == guidFilterLocalsPlusArgs)
        {
            //we create a special enumerator for this
            IDebugClassField* pfieldThis  = NULL;
            IEnumDebugFields* pparameters = NULL;
            IEnumDebugFields* plocals     = NULL;

            pmethod->GetThis( &pfieldThis );
            pmethod->EnumParameters( &pparameters );
            pmethod->EnumLocals( m_address, &plocals );

            CEnumMethodField* penumMethodField =
                new CEnumMethodField( pfieldThis, pparameters, plocals );
            if (pfieldThis != NULL)
                pfieldThis->Release();
            if (pparameters != NULL)
                pparameters->Release();
            if (plocals != NULL)
                plocals->Release();
            if (!penumMethodField)
            {
                hr = E_OUTOFMEMORY;
            }
            else
            {
                hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                penumMethodField->Release();
            }
        }
        else if (guidFilter == guidFilterThis )
        {
            IDebugClassField* pfieldThis = NULL;

            hr = pmethod->GetThis( &pfieldThis );
            if (SUCCEEDED(hr))
            {
                CEnumMethodField* penumMethodField =
                    new CEnumMethodField( pfieldThis, NULL, NULL );
                pfieldThis->Release();
                if (!penumMethodField)
                {
                    hr = E_OUTOFMEMORY;
                }
                else
                {
                    hr = penumMethodField->QueryInterface( IID_IEnumDebugFields,
                        reinterpret_cast<void**>(&pfields) );
                    penumMethodField->Release();
                }
            }
        }
        else
        {
            hr = E_FAIL;
        }

        pmethod->Release();
        if (hr != S_OK)
            return hr;
    }

    //create a property info enumeration around the field enumerator
    CEnumPropertyInfo* pproperties =
        new CEnumPropertyInfo( m_provider, m_address, m_binder,
                               radix, pfields, infoFlags );
    if (pfields != NULL)
        pfields->Release();
    if (pproperties == NULL)
        return E_OUTOFMEMORY;

    hr = pproperties->QueryInterface( IID_IEnumDebugPropertyInfo2,
        reinterpret_cast<void**>(ppchildren) );
    pproperties->Release();

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [Ejemplo de implementación de locales](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)
- [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
