---
title: IDebugSymbolProvider::GetAddressesFromPosition ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27767af36093e9424775074a55bafadac9a4480d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719405"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Este método asigna una posición de documento en una matriz de direcciones de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parámetros
`pDocPos`\
[en] La posición del documento.

`fStatmentOnly`\
[en] Si es TRUE, limita las direcciones de depuración a una sola instrucción.

`ppEnumBegAddresses`\
[fuera] Devuelve un enumerador para las direcciones de depuración iniciales asociadas a esta instrucción o línea.

`ppEnumEndAddresses`\
[fuera] Devuelve un [enumerador IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) para las direcciones de depuración final asociadas a esta instrucción o línea.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una posición de documento normalmente indica un rango de líneas de origen. Este método proporciona las direcciones de depuración inicial y final asociadas a estas líneas. Algunos lenguajes permiten instrucciones que abarcan varias líneas o líneas que contienen más de una instrucción. Este método proporciona una marca para limitar las direcciones de depuración a una sola instrucción.

 Es posible que una sola instrucción tenga varias direcciones de depuración, como en el caso de las plantillas.

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
