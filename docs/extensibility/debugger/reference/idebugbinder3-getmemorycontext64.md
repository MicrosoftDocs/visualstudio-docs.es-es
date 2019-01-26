---
title: IDebugBinder3::GetMemoryContext64 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 605effa6f8970b1a89601e72837d4ab7ab352f79
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976672"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
Convierte una ubicación del objeto o una dirección de memoria de 64 bits en un contexto de la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMemoryContext64 (  
   IDebugField*           pField,  
   UINT64                 uConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext64 (  
   IDebugField              pField,  
   ulong                    uConstant,  
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el objeto que se va a buscar. Si `NULL`, a continuación, utilice `dwConstant` en su lugar.  
  
 `uConstant`  
 [in] Una dirección de memoria de 64 bits, como 0x50000000.  
  
 `ppMemCxt`  
 [out] Devuelve el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfaz que representa la dirección del objeto o la dirección en la memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes se crea un objeto que implementa el [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md) interfaz y utiliza este método para recuperar el contexto de la memoria.  
  
```cpp  
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )  
{  
    // precondition  
    REQUIRE( NULL != out_ppMemoryContext );  
  
    if (NULL == out_ppMemoryContext)  
        return E_POINTER;  
  
    *out_ppMemoryContext = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (VT_EMPTY == this->m_VarValue.vt)  
    {  
        return E_FAIL;  
    }  
  
    // function body  
    if (NULL != this->m_pBinder)  
    {  
        UINT64 dwOffset = 0;  
  
        DEBUG_PROPERTY_INFO dpInfo;  
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,  
                                           10, // RADIX  
                                           DEFAULT_TIMEOUT,  
                                           NULL,  
                                           0,  
                                           &dpInfo);  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != dpInfo.bstrValue );  
            REQUIRE( NULL == dpInfo.bstrName );  
            REQUIRE( NULL == dpInfo.bstrFullName );  
            REQUIRE( NULL == dpInfo.bstrType );  
            REQUIRE( NULL == dpInfo.pProperty );  
  
            wchar_t * end;  
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output  
            ::SysFreeString(dpInfo.bstrValue);  
        }  
  
        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)  
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);  
        else  
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);  
  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != *out_ppMemoryContext );  
        }  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    HRESULT HR = E_FAIL;  
  
    if (NULL != *out_ppMemoryContext)  
    {  
        HR = S_OK;  
    }  
  
    return HR;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)