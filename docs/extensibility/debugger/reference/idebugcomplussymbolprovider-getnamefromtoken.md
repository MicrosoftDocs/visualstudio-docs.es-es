---
title: IDebugComPlusSymbolProvider::GetNameFromToken | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetNameFromToken
- GetNameFromToken
ms.assetid: 6e8cf468-5fd1-4655-93ed-88828d6068b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26bb20ec3db39f7dfdcb8083e56e711c46eb60f8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206372"
---
# <a name="idebugcomplussymbolprovidergetnamefromtoken"></a>IDebugComPlusSymbolProvider::GetNameFromToken
Devuelve el nombre asociado con el token especificado, dado su objeto de metadatos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNameFromToken (
    IUnknown* pMetadataImport,
    DWORD     dwToken,
    BSTR*     pbstrName
);
```

```csharp
int GetNameFromToken (
    object     pMetadataImport,
    uint       dwToken,
    out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pMetadataImport`\
[in] Objeto que contiene la información de metadatos.

`dwToken`\
[in] Símbolo (token) que el nombre.

`pbstrName`\
[out] Nombre que se corresponde con el token.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.

```cpp
HRESULT CDebugSymbolProvider::GetNameFromToken(
    IUnknown* pMetadataImport,
    DWORD dwToken,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetaData;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY(CDebugSymbolProvider::GetNameFromToken);

    IfFalseGo( pMetadataImport && pbstrName, E_INVALIDARG );

    *pbstrName = NULL;
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**) &pMetaData ) );

    switch ( TypeFromToken(dwToken) )
    {
        case mdtModule:
            IfFailGo( GetModuleName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtTypeDef:
            IfFailGo( GetTypeName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtFieldDef:
            IfFailGo( GetFieldName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtMethodDef:
            IfFailGo( GetMethodName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtEvent:
            IfFailGo( GetEventName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtProperty:
            IfFailGo( GetPropertyName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtAssembly:
            IfFailGo( GetAssemblyName( pMetaData, dwToken, pbstrName) );
            break;

        default:
            ASSERT(!"Unsupported token passed to GetNameFromToken");
            hr = E_FAIL;
            break;
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetNameFromToken, hr);
    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
