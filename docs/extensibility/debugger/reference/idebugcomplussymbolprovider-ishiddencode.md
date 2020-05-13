---
title: IDebugComPlusSymbolProvider::IsHiddenCode ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsHiddenCode
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1ede1cbd8c2a69d45a8c653aa97d0bfb618f821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733664"
---
# <a name="idebugcomplussymbolproviderishiddencode"></a>IDebugComPlusSymbolProvider::IsHiddenCode
Determina si el código en la dirección del depurador especificada está oculto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsHiddenCode(
    IDebugAddress* pAddress
);
```

```csharp
int IsHiddenCode(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[en] La dirección de depuración representada por un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.

## <a name="return-value"></a>Valor devuelto
Si el código está `S_OK`oculto, devuelve ; de lo `S_FALSE`contrario, devuelve .

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.

```cpp
HRESULT CDebugSymbolProvider::IsHiddenCode(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,
                                address.addr.addr.addrMethod.dwVersion,
                                address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this sequence point is not hidden

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
