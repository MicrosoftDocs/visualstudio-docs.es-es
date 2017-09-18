---
title: "IDebugComPlusSymbolProvider::GetAssemblyName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::GetAssemblyName"
  - "GetAssemblyName"
ms.assetid: a08cd609-b9b9-47bd-bf73-cbf851285907
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider::GetAssemblyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera el nombre del ensamblado especificado el módulo y dominio de aplicación.  
  
## Sintaxis  
  
```  
[C++]  
HRESULT GetAssemblyName(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule,  
   BSTR*   pbstrName  
);  
```  
  
```  
[C#]  
int GetAssemblyName(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   string pbstrName  
);  
```  
  
#### Parámetros  
 `ulAppDomainID`  
 \[in\]  Identificador del dominio de aplicación.  
  
 `guidModule`  
 \[in\]  identificador único para el módulo.  
  
 `pbstrName`  
 \[out\]  Devuelve el nombre del ensamblado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto **de CDebugSymbolProvider** que expone la interfaz de [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAssemblyName(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    BSTR* pbstrName  
)  
{  
    HRESULT hr = S_OK;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    CComPtr<IMetaDataImport> pMetadata;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetMetadataForModule );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    *pbstrName = NULL;  
  
    IfFailGo( GetMetadata( idModule, &pMetadata ) );  
    IfFailGo( GetAssemblyName( pMetadata, 0, pbstrName ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetMetadataForModule, hr );  
    return hr;  
}  
```  
  
## Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)