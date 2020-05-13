---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44dceaa8b5cffd3bd81b7e8527368c38a6faaf18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734160"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Determina si los símbolos de depuración se cargan para el módulo especificado dado el identificador de dominio de aplicación.

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

## <a name="parameters"></a>Parámetros
`ulAppDomainID`\
[en] Identificador del dominio de aplicación.

`guidModule`\
[en] Identificador único para el módulo.

## <a name="return-value"></a>Valor devuelto
Si se cargan los `S_OK`símbolos de depuración, devuelve ; de lo `S_FALSE`contrario, devuelve .

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz.

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
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
