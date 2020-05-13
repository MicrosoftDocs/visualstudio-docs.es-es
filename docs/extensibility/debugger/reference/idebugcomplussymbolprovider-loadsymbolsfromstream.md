---
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d208f8ce04e884c9dfb3b8b272271e686e3b2762
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733610"
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Carga símbolos de depuración dado el flujo de datos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LoadSymbolsFromStream(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStream(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    IStream pStream
);
```

## <a name="parameters"></a>Parámetros
`ulAppDomainID`\
[en] Identificador del dominio de aplicación.

`guidModule`\
[en] Identificador único del módulo.

`baseAddress`\
[en] Dirección de memoria base.

`pUnkMetadataImport`\
[en] Objeto que contiene los metadatos del símbolo.

`pStream`\
[en] Flujo de datos que contiene los símbolos.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un **CDebugSymbolProvider** objeto que expone el [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaz. El método llama al método [LoadSymbolsFromStreamWithCorModule.](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IStream* pStream
)
{
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);
}
```

## <a name="see-also"></a>Vea también
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
