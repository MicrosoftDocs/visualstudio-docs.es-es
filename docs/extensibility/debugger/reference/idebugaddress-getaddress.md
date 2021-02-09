---
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
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853017"
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

## <a name="remarks"></a>Notas
 La estructura de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) se pasa a este método, que, a su vez, la rellena con la información adecuada. La forma en que se interpreta esta información depende del tipo de información devuelta y del propio controlador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obtener más detalles.

## <a name="see-also"></a>Vea también
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
