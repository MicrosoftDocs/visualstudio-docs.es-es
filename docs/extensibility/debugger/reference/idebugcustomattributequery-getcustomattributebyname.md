---
title: IDebugCustomAttributeQuery::GetCustomAttributeByName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery::GetCustomAttributeByName
- GetCustomAttributeByName
ms.assetid: 6779727c-d10a-4abe-9acd-d0a1eb0737e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e452b0e1ab6de862723cfdc36f7b7226a01d676
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributequerygetcustomattributebyname"></a>IDebugCustomAttributeQuery::GetCustomAttributeByName
Recupera un atributo personalizado, dado su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCustomAttributeByName(  
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   string    pszCustomAttributeName,  
   ref int[] ppBlob,  
   out uint  pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCustomAttributeName`  
 [in] Nombre del atributo personalizado.  
  
 `ppBlob`  
 [entrada, salida] Matriz de bytes que contiene los datos del atributo personalizado.  
  
 `pdwLen`  
 [out] Longitud en bytes de la `ppBlob` parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Si el atributo personalizado no existe, devuelve `S_FALSE`. De lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugClassFieldSymbol** objeto que expone la [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md) interfaz.  
  
```cpp  
HRESULT CDebugClassFieldSymbol::GetCustomAttributeByName(  
    LPCOLESTR pszCustomAttributeName,  
    BYTE *pBlob,  
    DWORD *pdwLen  
)  
{  
    HRESULT hr = S_FALSE;  
    CComPtr<IMetaDataImport> pMetadata;  
    mdToken token = mdTokenNil;  
    CComPtr<IDebugField> pField;  
    CComPtr<IDebugCustomAttributeQuery> pCA;  
  
    ASSERT(IsValidWideStringPtr(pszCustomAttributeName));  
    ASSERT(IsValidWritePtr(pdwLen, ULONG*));  
  
    METHOD_ENTRY( CDebugClassFieldSymbol::GetCustomAttributeByName );  
  
    IfFalseGo( pszCustomAttributeName && pdwLen, E_INVALIDARG );  
  
    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );  
  
    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );  
    IfFailGo( CDebugCustomAttribute::GetCustomAttributeByName( pMetadata,  
              token,  
              pszCustomAttributeName,  
              pBlob,  
              pdwLen ) );  
Error:  
  
    METHOD_EXIT( CDebugClassFieldSymbol::GetCustomAttributeByName, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)