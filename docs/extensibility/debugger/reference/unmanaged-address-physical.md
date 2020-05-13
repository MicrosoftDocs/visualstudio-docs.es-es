---
title: UNMANAGED_ADDRESS_PHYSICAL Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9070fcfbf79fb96ecff87a793c221f3e7a65c2ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713285"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
Esta estructura representa una dirección física.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Miembros
 `offset`\
 Un desplazamiento de 64 bits en un espacio de direcciones físico.

## <a name="remarks"></a>Observaciones
 Esta estructura forma parte de la unión en `DEBUG_ADDRESS_UNION` la estructura `ADDRESS_KIND_UNMANAGED_PHYSICAL` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando se establece el `dwKind` campo de la estructura en (un valor de la [enumeración ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
