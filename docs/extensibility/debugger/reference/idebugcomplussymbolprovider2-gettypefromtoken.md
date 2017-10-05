---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b8395849f002519d52ed1f547e92b67e35f6408e
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
Recupera un tipo dado su token.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetTypeFromToken(  
   ULONG32       appDomain,  
   GUID          guidModule,  
   DWORD         tdToken,  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetTypeFromToken(  
   uint            appDomain,  
   Guid            guidModule,  
   uint            tdToken,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `appDomain`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `tdToken`  
 [in] Símbolo (token) del tipo que se va a recuperar.  
  
 `ppField`  
 [out] Devuelve el tipo representado por la [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetTypeFromToken(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    DWORD tdToken,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
