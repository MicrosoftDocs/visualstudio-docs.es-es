---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- LoadSymbolsFromCallback
- IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
ms.assetid: 905315ba-8e9b-4889-b9da-98e1441950ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 767c9218e8b666eb1f27891bd84ae110befbb798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromcallback"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
Mediante el método de devolución de llamada especificado de símbolos de depuración de carga.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT LoadSymbolsFromCallback(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   BSTR      bstrModuleName,  
   BSTR      bstrSymSearchPath,  
   IUnknown* pCallback  
);  
```  
  
```csharp  
int LoadSymbolsFromCallback(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   object pUnkMetadataImport,  
   object pUnkCorDebugModule,  
   string bstrModuleName,  
   string bstrSymSearchPath,  
   object pCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador del dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `pUnkMetadataImport`  
 [in] Objeto que contiene los metadatos de símbolos.  
  
 `pUnkCorDebugModule`  
 [in] Objeto que implementa el [ICorDebugModule (interfaz)](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `bstrModuleName`  
 [in] Nombre del módulo.  
  
 `bstrSymSearchPath`  
 [in] Ruta de acceso para buscar el archivo de símbolos.  
  
 `pCallback`  
 [in] Objeto que representa el método de devolución de llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone la [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interfaz.  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbolsFromCallback(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IUnknown *pMetadataImport,  
    IUnknown * _pCorModule,  
    BSTR bstrModule,  
    BSTR bstrSearchPath,  
    IUnknown *pCallback)  
{  
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");  
    USES_CONVERSION;  
    EmitTickCount(W2A(bstrModule));  
  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    bool fSymbolsLoaded = false;  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pMetadataImport, E_INVALIDARG );  
    IfFalseGo( _pCorModule, E_INVALIDARG );  
  
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,  
                                           (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    //  
    //  We are now allowing modules to be created that do not have SymReaders.  
    //  It is likely there are a number of corner cases being ignored  
    //  that will require knowledge of the hr result below.  
    //  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
    HRESULT hrLoad = pmoduleNew->Create( idModule,  
                                         dwCurrentState,  
                                         pMetadata,  
                                         pCorModule,  
                                         bstrModule,  
                                         bstrSearchPath,  
                                         pCallback );  
  
    if (hrLoad == S_OK)  
    {  
        fSymbolsLoaded = true;  
    }  
  
    // Remove the old module  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule( pmodule );  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    if (SUCCEEDED(hr) && !fSymbolsLoaded)  
    {  
        hr = hrLoad;  
    }  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
    EMIT_TICK_COUNT("Exit");  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)