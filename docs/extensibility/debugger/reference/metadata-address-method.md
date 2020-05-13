---
title: METADATA_ADDRESS_METHOD de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc3dd7a34e4f9a3e1b933781aeaf4e18cad7ec17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714454"
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
 El identificador del método.

 [C++] `_mdToken` es `typedef` un para un `int`32-bit .

 `dwOffset`\
 El desplazamiento de la clase comienza a este método (puede representar el desplazamiento en la vtable).

 `dwVersion`\
 La versión del método (este valor es único para el proveedor de símbolos).

## <a name="remarks"></a>Observaciones
 Esta estructura forma parte de la unión en `DEBUG_ADDRESS_UNION` la estructura `ADDRESS_KIND_METHOD` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando se establece el `dwKind` campo de la estructura en (un valor de la [enumeración ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
