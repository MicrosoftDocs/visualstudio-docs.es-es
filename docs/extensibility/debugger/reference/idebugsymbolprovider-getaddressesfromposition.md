---
description: Este método asigna una posición de documento en una matriz de direcciones de depuración.
title: 'IDebugSymbolProvider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4437055ccd693b40fe4f1f7d6364d9601c827a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159684"
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
de Posición del documento.

`fStatmentOnly`\
de Si es TRUE, limita las direcciones de depuración a una única instrucción.

`ppEnumBegAddresses`\
enuncia Devuelve un enumerador para las direcciones de depuración de inicio asociadas a esta instrucción o línea.

`ppEnumEndAddresses`\
enuncia Devuelve un enumerador [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) para las direcciones de depuración finales asociadas a esta instrucción o línea.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una posición de documento suele indicar un intervalo de líneas de código fuente. Este método proporciona las direcciones de depuración inicial y final asociadas a estas líneas. Algunos lenguajes admiten instrucciones que abarcan varias líneas o líneas que contienen más de una instrucción. Este método proporciona una marca para limitar las direcciones de depuración a una única instrucción.

 Es posible que una sola instrucción tenga varias direcciones de depuración, como en el caso de las plantillas.

## <a name="see-also"></a>Consulte también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
