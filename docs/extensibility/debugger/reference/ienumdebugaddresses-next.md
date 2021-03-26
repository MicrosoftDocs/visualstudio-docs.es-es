---
description: Este método devuelve el siguiente conjunto de elementos de la enumeración addresses.
title: 'IEnumDebugAddresses:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570fbcb49e4e96fce558c5981eb590ae33e0f0a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083185"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Este método devuelve el siguiente conjunto de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

`rgelt`\
[in, out] Matriz de elementos [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que se va a rellenar.

`pceltFetched`\
enuncia Devuelve el número de elementos realmente devueltos en `rgelt` .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si se puede devolver menos que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
