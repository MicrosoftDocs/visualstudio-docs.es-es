---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e6b380d0522052597a77b0b1cc3bff1753d610de
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Determina si se cargan los símbolos de depuración para el módulo especificado según el identificador de dominio de aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT AreSymbolsLoaded (  
   ULONG32 ulAppDomainID,  
   GUID    guidModule  
);  
```  
  
```csharp  
int AreSymbolsLoaded (  
   uint ulAppDomainID,  
   Guid guidModule  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador para el dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único para el módulo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se cargan los símbolos de depuración, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(  
    ULONG32 ulAppDomainID,  
    GUID guidModule  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );  
  
    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)