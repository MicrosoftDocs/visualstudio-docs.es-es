---
title: "Implementaci&#243;n de cambiar los valores de ejemplo | Microsoft Docs"
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
  - "evaluación de expresiones, valores locales"
  - "depurar [SDK de depuración], la evaluación de expresiones"
ms.assetid: ee2d955b-12ca-4f27-89aa-c2d0e768b6b6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementaci&#243;n de cambiar los valores de ejemplo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cada local aparece en el **locales** ventana tiene un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado a él. Esto `IDebugProperty2` objeto contiene el nombre, valor y tipo de la local. Cuando un usuario cambia el valor de una variable local, Visual Studio llama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) para actualizar el valor de la variable local en la memoria. En este ejemplo, la variable local está representada por la `CFieldProperty` clase que implementa el `IDebugProperty2` interfaz.  
  
> [!NOTE]
>  Para **inspección** y **Inspección rápida** expresiones, el valor que se va a cambiar es representado por la `CValueProperty` clase en el ejemplo MyCEE. Sin embargo, la implementación de `IDebugProperty2::SetValueAsString` es la misma que se muestra aquí.  
  
 Esta implementación de `IDebugProperty2::SetValueAsString` realiza las siguientes tareas:  
  
1.  Evalúa la expresión para generar un valor.  
  
2.  Enlaza asociado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) a su ubicación de memoria de objetos y generar un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
3.  Convierte el valor en una serie de bytes.  
  
4.  Llamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para almacenar los bytes en la memoria.  
  
## Código administrado  
 Se trata de una implementación de `IDebugProperty2::SetValueAsString` en código administrado.  
  
```  
[C#]  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT SetValueAsString(  
            string pszValue,  
            uint   dwRadix,  
            uint   dwTimeout)  
        {  
            HRESULT hr = COM.E_NOTIMPL;  
            uint flags = (uint)enum_PARSEFLAGS.PARSE_EXPRESSION;  
            CParsedExpression parsedExpression =  
                new CParsedExpression(flags, dwRadix, pszValue);  
            IDebugProperty2 value;  
            parsedExpression.EvaluateSync(flags,  
                                          dwTimeout,  
                                          null,  
                                          null,  
                                          null,  
                                          "string",  
                                          out value);  
            if (value != null)  
            {  
                DEBUG_PROPERTY_INFO[] dpi = new DEBUG_PROPERTY_INFO[1];  
                hr = value.GetPropertyInfo(  
                    (uint)enum_DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE,  
                    dwRadix,  
                    dwTimeout,  
                    null,  
                    0,  
                    dpi);  
                if (hr == COM.S_OK)  
                {  
                    hr = Field.SetValue(binder,  
                                        field,  
                                        dpi[0].bstrValue);  
                }  
            }  
            return hr;  
        }  
    }  
  
//----------------------------------------------------------------------------  
  
    internal class Field  
    {  
        internal static HRESULT SetValue(  
            IDebugBinder binder,  
            IDebugField  field,  
            string       bstrValue)  
        {  
            HRESULT hr = COM.E_FAIL;  
            uint fieldSize = 0;  
            Type fieldType = GetType(field, out fieldSize);  
            if (fieldType != null)  
            {  
                FIELD_INFO[] fi = new FIELD_INFO[1];  
                hr = field.GetInfo((uint)enum_FIELD_INFO_FIELDS.FIF_MODIFIERS, fi);  
                if (hr != COM.S_OK ||  
                   (fi[0].dwModifiers & (uint)enum_FIELD_MODIFIERS.FIELD_MOD_CONSTANT) != 0)  
                {  
                    // Couldn't get field info or field is constant and can't be changed.  
                    return COM.E_FAIL;  
                }  
                IDebugObject valueObject;  
                IntPtr pBuffer = new IntPtr();  
                int bufferSize = 0;  
                binder.Bind(null, field, out valueObject);  
                if (valueObject != null)  
                {  
                    if (fieldType == typeof(sbyte))  
                    {  
                        sbyte value = Convert.ToSByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(short))  
                    {  
                        System.Int16 value = Convert.ToInt16(bstrValue);  
                        bufferSize = 2;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(int))  
                    {  
                        System.Int32 value = Convert.ToInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(long))  
                    {  
                        System.Int64 value = Convert.ToInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(byte))  
                    {  
                        byte value = Convert.ToByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(char))  
                    {  
                        char value = Convert.ToChar(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(bool))  
                    {  
                        bool value = Convert.ToBoolean(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(uint))  
                    {  
                        System.UInt32 value = Convert.ToUInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                   if (fieldType == typeof(ulong))  
                   {  
                        System.UInt64 value = Convert.ToUInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(float))  
                   {  
                        float value = Convert.ToSingle(bstrValue);  
                        bufferSize = sizeof(float);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(double))  
                   {  
                        double value = Convert.ToDouble(bstrValue);  
                        bufferSize = sizeof(double);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(string))  
                   {  
                        bufferSize = bstrValue.Length;  
                        pBuffer = Marshal.StringToCoTaskMemAuto(bstrValue);  
                   }  
                   if (bufferSize != 0)  
                   {  
                        byte[] byteBuffer = new byte[bufferSize];  
                        for (int i = 0; i < bufferSize; i++)  
                        {  
                            byteBuffer[i] = Marshal.ReadByte(pBuffer,i);  
                        }  
                        Marshal.FreeCoTaskMem(pBuffer);  
                        hr = valueObject.SetValue(byteBuffer, (uint)bufferSize);  
                    }  
                }  
            }  
            return hr;  
        }  
    }  
}  
```  
  
## Código no administrado  
 Se trata de una implementación de `IDebugProperty2::SetValueAsString` en código administrado. La función auxiliar `FieldCoerceValueType` \(no se muestra\) fuerza un `VARIANT` sea un tipo específico y hace que el valor es uno de los tipos de `FieldSetValue` puede controlar.  
  
```  
[C++]  
STDMETHODIMP CFieldProperty::SetValueAsString(   
        in LPCOLESTR pszValueStr,  
        in DWORD     radix,  
        in DWORD     timeout  
        )  
{  
    HRESULT hr;  
  
    //evaluate the value  
    VARIANT value;  
    hr = Evaluate( m_provider,  
                   m_address,  
                   m_binder,  
                   pszValueStr,  
                   NULL,  
                   &value );  
    if (FAILED(hr))  
        return hr;  
    if (hr == S_FALSE)  
        return E_FAIL;   //parse failed  
  
    //copy the bits  
    hr = FieldSetValue( m_binder, m_field, value );  
  
    return hr;  
}  
  
//----------------------------------------------------------------------------  
  
HRESULT FieldSetValue(  
        in IDebugBinder* pbinder,  
        in IDebugField*  pfield,  
        in VARIANT&      rawValue )  
{  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT       hr      = S_OK;  
    IDebugObject* pobject = NULL;  
    VARIANT       value;  
    VariantInit(&value);  
  
    //check the type  
    hr = FieldCoerceValueType( pbinder, pfield, rawValue, &value );  
    if (FAILED(hr))  
        goto fail;  
    if (hr == S_FALSE)  
    {  
        VariantClear(value);  
        return E_FAIL;  
    }  
  
    //get the object  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        VariantClear(value);  
        return hr;  
    }  
  
    //set the value  
    switch (value.vt)  
    {  
        case VT_BSTR:  
        {  
            if (value.bstrVal == NULL)  
            {  
                LPOLESTR pszEmptyStr = OLE("");  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(pszEmptyStr),  
                     sizeof(OLECHAR) );  
            }  
            else  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(value.bstrVal),  
                    (SysStringLen(value.bstrVal)+1) * sizeof(wchar_t));  
        }  
  
        case VT_BOOL:  
        case VT_I1:  
        case VT_UI1:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 1 );  
            break;  
  
        case VT_I2:  
        case VT_UI2:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 2 );  
            break;  
  
        case VT_I4:  
        case VT_UI4:  
        case VT_R4:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 4 );  
            break;  
  
        case VT_I8:  
        case VT_UI8:  
        case VT_R8:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 8 );  
            break;  
  
        case VT_VOID:  
        case VT_EMPTY:  
            hr = E_FAIL;  
            break;  
  
        case VT_UNKNOWN:  
        {  
            //this is also a field (structured type)  
            if (value.punkVal == NULL)  
            {  
                pobject->Release();  
                VariantClear(value);  
                return E_FAIL;  
            };  
  
            IDebugField* valueField;  
            hr = value.punkVal->QueryInterface( IID_IDebugField,  
                reinterpret_cast<void**>(&valueField) );  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            //for MyC we simply copy the bits  
            IDebugObject* valueObject;  
            hr = pbinder->Bind( NULL, valueField, &valueObject );  
            valueField->Release();  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            BYTE* pvalueBits;  
            UINT  valueSize;  
            hr = valueObject->GetSize( &valueSize );  
            if (FAILED(hr))  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            pvalueBits = NALLOC(BYTE,valueSize+1);  
            if (!pvalueBits)  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return E_OUTOFMEMORY;  
            };  
  
            hr = valueObject->GetValue( pvalueBits, valueSize );  
            valueObject->Release();  
            if (FAILED(hr))  
            {  
                free(pvalueBits);  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            hr = pobject->SetValue( pvalueBits, valueSize );  
            free(pvalueBits);  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            break;  
        }  
  
        default:  
            //not a primitive type  
            hr = E_FAIL;  
            break;  
    }  
  
    VariantClear( &value );  
    pobject->Release();  
    return hr;  
}  
  
```  
  
## Vea también  
 [Cambiar el valor de una variable Local](../../extensibility/debugger/changing-the-value-of-a-local.md)   
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)