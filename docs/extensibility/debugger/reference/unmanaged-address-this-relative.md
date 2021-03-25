---
description: Esta estructura representa una dirección relativa a un puntero this (me en Visual Basic).
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe63edeed68bc50aae0062f171f66c8a9203ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070679"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Esta estructura representa una dirección relativa a un `this` puntero ( `Me` en Visual Basic).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>Miembros
 `dwOffset`\
 Desplazamiento de bytes desde una posición base (por ejemplo, el inicio de una clase vtable).

 `dwBitOffset`\
 Desplazamiento en bits desde una posición base (siempre es 0 a menos que se refiera a un campo de bits).

 `dwBitLength`\
 Número de bits que representa la dirección (siempre es 0 a menos que se hace referencia a un campo de bits).

## <a name="remarks"></a>Observaciones
 Esta estructura forma parte de la Unión de la estructura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura se establece en `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (un valor de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
