---
description: Esta estructura representa la dirección de un método de una clase.
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40047dbdb35ad5958e923bb9a3ec18faa0d69be6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075476"
---
# <a name="metadata_address_method"></a>METADATA_ADDRESS_METHOD
Esta estructura representa la dirección de un método de una clase.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>Miembros
 `tokMethod`\
 IDENTIFICADOR del método.

 [C++] `_mdToken` es un `typedef` para un 32 bits `int` .

 `dwOffset`\
 El desplazamiento de la clase comienza a este método (puede representar el desplazamiento en vtable).

 `dwVersion`\
 Versión del método (este valor es único para el proveedor de símbolos).

## <a name="remarks"></a>Observaciones
 Esta estructura forma parte de la Unión de la estructura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura se establece en `ADDRESS_KIND_METHOD` (un valor de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
