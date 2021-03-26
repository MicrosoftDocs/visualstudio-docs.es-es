---
description: Asigna una posición de documento del módulo especificado a una matriz de direcciones de depuración.
title: IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAddressesInModuleFromPosition
- IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
ms.assetid: f901c66e-f53c-4ea0-8004-d8fcbf46f916
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d19b54e5e2d35791d160c5deb6eb06ee0431f978
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088216"
---
# <a name="idebugcomplussymbolprovidergetaddressesinmodulefromposition"></a>IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition
Asigna una posición de documento del módulo especificado a una matriz de direcciones de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAddressesInModuleFromPosition(
   ULONG32                  ulAppDomainID,
   GUID                     guidModule,
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesInModuleFromPosition(
   uint                    ulAppDomainID,
   Guid                    guidModule,
   IDebugDocumentPosition2 pDocPos,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parámetros
`ulAppDomainID`\
de Identificador del dominio de aplicación.

`guidModule`\
de Identificador único del módulo.

`pDocPos`\
de Posición del documento.

`fStatmentOnly`\
de Si es `TRUE` , limita las direcciones de depuración a una única instrucción.

`ppEnumBegAddresses`\
enuncia Devuelve un enumerador para las direcciones de depuración de inicio asociadas a esta instrucción o línea.

`ppEnumEndAddresses`\
enuncia Devuelve un enumerador para las direcciones de depuración finales asociadas a esta instrucción o línea.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo implementar este método para un objeto **CDebugSymbolProvider** que expone la interfaz [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .

```cpp
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

## <a name="see-also"></a>Consulte también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
