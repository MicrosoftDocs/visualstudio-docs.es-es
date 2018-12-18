---
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3897e9d54bf9ac2a50b40da68a9d8430685631c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728407"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Asigna una posición de documento en el módulo especificado en una matriz de direcciones de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
[C++]  
HRESULT GetAddressesInModuleFromPosition(  
   ULONG32                  ulAppDomainID,  
   GUID                     guidModule,  
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```  
[C#]  
int GetAddressesInModuleFromPosition(  
   uint                    ulAppDomainID,  
   Guid                    guidModule,  
   IDebugDocumentPosition2 pDocPos,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ulAppDomainID`  
 [in] Identificador de dominio de aplicación.  
  
 `guidModule`  
 [in] Identificador único del módulo.  
  
 `pDocPos`  
 [in] La posición del documento.  
  
 `fStatmentOnly`  
 [in] Si `TRUE`, limita las direcciones de depuración para una sola instrucción.  
  
 `ppEnumBegAddresses`  
 [out] Devuelve un enumerador para las direcciones iniciales de depuración que están asociadas con esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 [out] Devuelve un enumerador para las direcciones de depuración final que están asociadas con esta instrucción o línea.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPosition(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    GUID guidNULL = {0};  
  
    if (guidNULL == guidModule)  
    {  
        return GetAddressesInAppDomainFromPosition( ulAppDomainID,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
    else  
    {  
        return GetAddressesInModuleFromPositionHelper( ulAppDomainID,  
                guidModule,  
                pDocPos,  
                fStatementOnly,  
                ppEnumBegAddresses,  
                ppEnumEndAddresses );  
    }  
}  
  
HRESULT CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugDocumentPosition2* pDocPos,  
    BOOL fStatementOnly,  
    IEnumDebugAddresses** ppEnumBegAddresses,  
    IEnumDebugAddresses** ppEnumEndAddresses  
)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrFileName;  
    TEXT_POSITION posBeg;  
    TEXT_POSITION posEnd;  
    DWORD dwLine;  
    USHORT segRet = 0;  
    ULONG offRet = 0;  
    CAddrList listAddr;  
    CAddrList listAddrEnd;  
    CAddrList* plistAddrEnd = NULL;  
    bool fFileFound = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwListCount;  
    bool fFoundAddresses = false;  
    CComPtr<CModule> pmodule;  
    DWORD dwBegCol = 0;  
    DWORD dwEndCol = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pDocPos, IDebugDocumentPosition2));  
    ASSERT(IsValidWritePtr(ppEnumBegAddresses, IEnumDebugAddresses*));  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper);  
  
    // Bail on Invalid Args  
  
    IfFalseGo( pDocPos && ppEnumBegAddresses, E_INVALIDARG );  
  
    *ppEnumBegAddresses = NULL;  
    if (ppEnumEndAddresses)  
    {  
        *ppEnumEndAddresses = NULL;  
        plistAddrEnd = &listAddrEnd;  
    }  
  
    // Get the Position  
  
    IfFailGo( pDocPos->GetFileName(&bstrFileName) );  
    IfFailGo( pDocPos->GetRange(&posBeg, &posEnd) );  
  
    // Iterate over the module list accumulating addresses  
    // that match the position  
  
    dwLine = posBeg.dwLine;  
    IfFailGo( GetModule( idModule, &pmodule ) );  
    dwListCount = listAddr.GetCount();  
  
    if ( fStatementOnly )  
    {  
        dwBegCol = posBeg.dwColumn;  
        dwEndCol = posBeg.dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
    }  
    else  
    {  
        dwBegCol = 0;  
        dwEndCol = DWORD( -1);  
    }  
  
    while (!fFoundAddresses && dwLine <= posEnd.dwLine )  
    {  
        hr = pmodule->GetAddressesFromLine( bstrFileName,  
                                            dwLine,  
                                            posEnd.dwLine,  
                                            dwBegCol,  
                                            dwEndCol,  
                                            &listAddr,  
                                            plistAddrEnd );  
  
        dwLine++;  
        dwBegCol = 0;  
        dwEndCol = dwLine == posEnd.dwLine ? posEnd.dwColumn : DWORD( -1);  
  
        if (hr == E_SH_INVALID_POSITION)  
        {  
            fFileFound = true;  
            break;  
        }  
  
        if (FAILED(hr))  
        {  
            // Move on to the next module  
            break;  
        }  
  
        fFileFound = true;  
        fFoundAddresses = listAddr.GetCount() != dwListCount;  
    }  
  
    // Distinguish no file from bad position in the file  
    IfFalseGo( fFileFound, E_SH_FILE_NOT_FOUND);  
  
    // If the list is empty the position is bad  
    IfFalseGo( listAddr.GetCount(), E_SH_INVALID_POSITION );  
  
    // Create enumerators  
    IfFailGo( CreateEnumerator( ppEnumBegAddresses, &listAddr ) );  
    if (ppEnumEndAddresses)  
    {  
        IfFailGo( CreateEnumerator( ppEnumEndAddresses, &listAddrEnd ) );  
    }  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetAddressesInModuleFromPositionHelper, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

