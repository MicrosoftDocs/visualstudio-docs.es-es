---
title: DEBUG_ADDRESS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737513"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
Esta estructura representa una dirección.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>Miembros
`ulAppDomainID`\
El id. de proceso.

`guidModule`\
Guid del módulo que contiene esta dirección.

`tokClass`\
El token que identifica la clase o el tipo de esta dirección.

> [!NOTE]
> Este valor es específico de un proveedor de símbolos y, por lo tanto, no tiene ningún significado general que no sea como identificador para un tipo de clase.

`addr`\
Una [estructura DEBUG_ADDRESS_UNION,](../../../extensibility/debugger/reference/debug-address-union.md) que contiene una unión de estructuras que describen los tipos de dirección individuales. El `addr`valor .`dwKind` proviene de la enumeración [ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) que explica cómo interpretar la unión.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa a la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método que se va a rellenar.

**Advertencia [sólo C++]**

Si `addr.dwKind` `ADDRESS_KIND_METADATA_LOCAL` es `addr.addr.addrLocal.pLocal` y si no es un `Release` valor nulo, debe llamar al puntero de token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
