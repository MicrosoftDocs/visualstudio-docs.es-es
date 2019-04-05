---
title: Enumerar variables locales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enumerating locals
- expression evaluation, enumerating locals
ms.assetid: 254a88e7-d3a7-447a-bd0c-8985e73d85cf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 422a641455d6b706250ca34e3857c3e8d21920ca
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58995108"
---
# <a name="enumerating-locals"></a>Enumeración de variables locales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando Visual Studio esté listo para rellenar el **variables locales** ventana, llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto desde [ GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) (consulte [implementación de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)). `IDebugProperty2::EnumChildren` Devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto.  
  
 Esta implementación de `IDebugProperty2::EnumChildren` realiza las siguientes tareas:  
  
1.  Garantiza que esto representa un método.  
  
2.  Usa el `guidFilter` argumento para determinar qué método debe llamar en el [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Si `guidFilter` es igual a:  
  
    1.  `guidFilterLocals`, llame a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) para obtener un [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) objeto.  
  
    2.  `guidFilterArgs`, llame a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) para obtener un `IEnumDebugFields` objeto.  
  
    3.  `guidFilterLocalsPlusArgs`, sintetizar una enumeración que combina los resultados de `IDebugMethodField::EnumLocals` y `IDebugMethodField::EnumArguments`. Esta síntesis está representada por la clase `CEnumMethodField`.  
  
3.  Crea una instancia de una clase (llamado `CEnumPropertyInfo` en este ejemplo) que implementa el `IEnumDebugPropertyInfo2` interfaz y contiene el `IEnumDebugFields` objeto.  
  
4.  Devuelve el `IEnumDebugProperty2Info2` interfaz desde el `CEnumPropertyInfo` objeto.  
  
## <a name="managed-code"></a>Código administrado  
 En este ejemplo se muestra una implementación de `IDebugProperty2::EnumChildren` en código administrado.  
  
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
                    IDebugClassField fieldThis   = null;  
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
                    IDebugClassField fieldThis   = null;  
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
 En este ejemplo se muestra una implementación de `IDebugProperty2::EnumChildren` en código no administrado.  
  
```cpp#  
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
            IDebugClassField* pfieldThis  = NULL;  
  
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
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Implementación de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)   
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
