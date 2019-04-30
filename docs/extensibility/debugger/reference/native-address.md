---
title: NATIVE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NATIVE_ADDRESS
helpviewer_keywords:
- NATIVE_ADDRESS structure
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d7d061d7cd60444a523d5764c30b7ff538faefe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913774"
---
# <a name="nativeaddress"></a>NATIVE_ADDRESS

Esta estructura representa una dirección nativa.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagNATIVE_ADDRESS {
    DWORD unknown;
} NATIVE_ADDRESS;
```

```csharp
public struct NATIVE_ADDRESS {
    public uint unknown;
}
```

## <a name="terms"></a>Términos

`unknown`

La dirección nativa (el significado de esto depende del tiempo de ejecución y el sistema operativo).

## <a name="remarks"></a>Comentarios

Esta estructura es parte de la unión en el [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando la `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura está establecida en `ADDRESS_KIND_NATIVE` (un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración).

## <a name="requirements"></a>Requisitos

Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
