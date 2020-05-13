---
title: IDebugComPlusSymbolProvider::GetArrayTypeFromAddress ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 048a086bae946b5ce730bdfe2c343b6cde1b29e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733990"
---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
Recupera información de tipo sobre la matriz especificada dada su dirección de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetArrayTypeFromAddress(
    IDebugAddress* pAddress,
    BYTE*          pSig,
    DWORD          dwSigLength,
    IDebugField**  ppField
);
```

```csharp
int GetArrayTypeFromAddress(
    IDebugAddress   pAddress,
    int[]           pSig,
    uint            dwSigLength,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[en] La dirección de depuración representada por un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaz.

`pSig`\
[en] Matriz que se está examinando.

`dwSigLength`\
[en] Longitud en bytes `pSig` de la matriz.

`ppField`\
[fuera] Devuelve el tipo de matriz representado por un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interfaz.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.

```cpp
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(
    IDebugAddress *pAddress,
    BYTE *pSig,
    DWORD dwSigLength,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    if ( S_OK == hr )
    {
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );

        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );
    RELEASE( pGenScope );
    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
