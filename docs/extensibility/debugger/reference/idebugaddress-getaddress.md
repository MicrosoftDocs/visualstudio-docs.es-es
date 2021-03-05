---
description: Devuelve una estructura que describe un objeto y su ubicación dentro de su ámbito o contenedor.
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52c52d12d8c357f4dbadeef673a3dc4474713ce9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145448"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Devuelve una estructura que describe un objeto y su ubicación dentro de su ámbito o contenedor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>Parámetros
`pAddress`\
[in, out] [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura rellenada por este método.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La estructura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) se pasa a este método, que, a su vez, la rellena con la información adecuada. La forma en que se interpreta esta información depende del tipo de información devuelta y del propio controlador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obtener más detalles.

## <a name="see-also"></a>Consulte también
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
