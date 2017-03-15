---
title: "IDebugComPlusSymbolProvider::GetAttributedClassesinModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::GetAttributedClassesinModule"
  - "GetAttributedClassesinModule"
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider::GetAttributedClassesinModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera las clases con el atributo especificado en un módulo especificado.  
  
## Sintaxis  
  
```  
[C++]  
HRESULT GetAttributedClassesinModule (  
   ULONG32            ulAppDomainID,  
   GUID               guidModule,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesinModule (  
   uint                 ulAppDomainID,  
   Guid                 guidModule,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `ulAppDomainID`  
 \[in\]  Identificador del dominio de aplicación.  
  
 `guidModule`  
 \[in\]  Identificador único del módulo.  
  
 `pstrAttribute`  
 \[in\]  La cadena del atributo.  
  
 `ppEnum`  
 \[out\]  Devuelve una enumeración de las clases con.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto **de CDebugSymbolProvider** que expone la interfaz de [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    CComPtr<IMetaDataImport> pMetaData;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    const void* pUnused;  
    ULONG cbUnused;  
    HCORENUM hEnum = 0;  
    ULONG cTypeDefs = 0;  
    ULONG cEnum;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );  
  
    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );  
    IfFailGo( GetModule( idModule, &pModule ) );  
    pModule->GetMetaData( &pMetaData );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       NULL,  
                                       0,  
                                       &cTypeDefs ) );  
  
    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
    pMetaData->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       rgTypeDefs,  
                                       cEnum,  
                                       &cTypeDefs ) );  
  
    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
    {  
  
        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                pstrAttribute,  
                &pUnused,  
                &cbUnused ) == S_OK)  
        {  
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)  
            {  
                ctField++;  
            }  
            else  
            {  
                ASSERT(!"Failed to Create Attributed Class");  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );  
  
    DELETERG( rgTypeDefs );  
  
    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)  
    {  
        RELEASE( rgFields[iTypeDef] );  
    }  
  
    DELETERG( rgFields );  
    RELEASE( pEnumFields );  
  
    return hr;  
}  
```  
  
## Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)