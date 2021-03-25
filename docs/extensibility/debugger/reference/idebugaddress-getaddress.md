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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094408"
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
