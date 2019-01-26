---
title: IDebugProperty3::SetValueAsStringWithError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::SetValueAsStringWithError
helpviewer_keywords:
- IDebugProperty3::SetValueAsStringWithError
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015781b266c01a108aaea6a5e56e19d9ff5fd89
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020274"
---
# <a name="idebugproperty3setvalueasstringwitherror"></a>IDebugProperty3::SetValueAsStringWithError
Establece el valor de esta propiedad y devuelve un mensaje de error, si es necesario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetValueAsStringWithError(  
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout,  
   BSTR*     errorString  
);  
```  
  
```csharp  
int SetValueAsStringWithError(  
   string     pszValue,  
   uint       dwRadix,  
   uint       dwTimeout,  
   out string errorString  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszValue`  
 [in] Valor que se va a establecer.  
  
 `dwRadix`  
 [in] La base del valor que se va a establecer.  
  
 `dwTimeout`  
 [in] La longitud de tiempo de espera para que se puede establecer el valor (`INFINITE` , espera indefinida).  
  
 `errorString`  
 [out] Si se produjo un error al establecer el valor, contiene el motivo del error.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor de entrada podría ser una expresión que se va a evaluar.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CProperty** objeto que expone el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz.  
  
```cpp  
HRESULT CProperty::SetValueAsStringWithError(   
    LPCOLESTR in_szValue,  
    DWORD in_RADIX,  
    DWORD in_TIMEOUT,   
    BSTR * out_ERRORTEXT  
)  
{  
    // precondition  
    REQUIRE( NULL != in_szValue );  
  
    if (NULL == in_szValue)  
        return E_INVALIDARG;  
  
    INVARIANT( this );  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)  
        return S_OK;  
  
    // function body  
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;  
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,  
                                       in_RADIX,  
                                       in_TIMEOUT,  
                                       NULL,  
                                       0,  
                                       &dpInfo);  
  
    if (ENSURE( S_OK == HR ))  
    {  
        REQUIRE( NULL != dpInfo.bstrFullName );  
        REQUIRE( NULL != dpInfo.bstrType );  
  
        REQUIRE( NULL == dpInfo.bstrName );  
        REQUIRE( NULL == dpInfo.bstrValue );  
        REQUIRE( NULL == dpInfo.pProperty );  
  
        BSTR bstrError = NULL;  
  
        UINT ichError = 0;  
        IDebugProperty2* pProperty = NULL;  
        IDebugParsedExpression* pParsedExpression = NULL;  
  
        CComBSTR bstrValue = dpInfo.bstrFullName;  
        bstrValue += L" = ";  
        bstrValue += in_szValue;  
        HR = this->m_pPropertyContext->m_pCEE->  
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);  
        if (S_OK == HR)  
        {  
            REQUIRE( NULL == bstrError );  
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,  
                                                 in_TIMEOUT,  
                                                 m_pPropertyContext->m_pSymbolProvider,  
                                                 m_pPropertyContext->m_pAddress,  
                                                 m_pPropertyContext->m_pBinder,  
                                                 NULL,  
                                                 &pProperty);  
  
            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;  
            if (pProperty)  
            {  
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);  
            }  
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)  
            {  
                HR = E_FAIL;  
                bstrError = dpInfo2.bstrValue;  
            }  
            else  
            {  
                ::SysFreeString(dpInfo.bstrValue);  
            }  
            EXTERNAL_RELEASE(pProperty);  
            EXTERNAL_RELEASE(pParsedExpression);          
        }  
  
        if (bstrError)  
        {  
            if(out_ERRORTEXT)  
            {  
                *out_ERRORTEXT = bstrError;  
                bstrError = NULL;  
            }  
            else  
            {  
                ::SysFreeString(bstrError);  
            }  
        }  
        ::SysFreeString(dpInfo.bstrFullName);  
        ::SysFreeString(dpInfo.bstrType);  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return HR;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)