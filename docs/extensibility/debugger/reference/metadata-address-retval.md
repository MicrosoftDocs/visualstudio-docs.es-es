---
title: METADATA_ADDRESS_RETVAL Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714271"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
Esta estructura representa un valor devuelto de un método o función.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>Miembros
 `tokMethod`\
 El identificador del método para el que está este valor devuelto es.

 `dwCorType`\
 El tipo base del valor devuelto. Se trata de `CorElementType` un valor de la enumeración definida en el archivo corhdr.h del SDK de .NET Framework.

 `dwSigSize`\
 El tamaño de la firma del `rgSig`valor devuelto (como se almacena en ).

 `rgSig`\
 Matriz de bytes que forma la firma del valor devuelto.

## <a name="remarks"></a>Observaciones
 Esta estructura forma parte de la unión en `DEBUG_ADDRESS_UNION` la estructura `ADDRESS_KIND_RETVAL` [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando se establece el `dwKind` campo de la estructura en (un valor de la [enumeración ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
