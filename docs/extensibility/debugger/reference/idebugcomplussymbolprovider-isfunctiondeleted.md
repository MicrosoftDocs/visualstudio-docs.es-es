---
title: IDebugComPlusSymbolProvider::IsFunctionDeleted | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionDeleted
ms.assetid: b276bd25-6658-4898-bc36-04ecdf92aa2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 504fa6855ad8b1fb38428e6e7ec7b3ac9721f644
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864262"
---
# <a name="idebugcomplussymbolproviderisfunctiondeleted"></a>IDebugComPlusSymbolProvider::IsFunctionDeleted
Determina que se ha eliminado la función en la dirección de depuración especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsFunctionDeleted(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsFunctionDeleted(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] La dirección de depuración representado por un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz. Esta dirección debe ser un METHOD_ADDRESS.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se elimina la función, devuelve `S_OK`. Si la función es existe, devuelve `S_FALSE`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::IsFunctionDeleted(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionDeleted );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsFunctionDeleted( address.addr.addr.addrMethod.tokMethod,  
                                     address.addr.addr.addrMethod.dwVersion,  
                                     address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates the function is not deleted  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsFunctionDeleted, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)