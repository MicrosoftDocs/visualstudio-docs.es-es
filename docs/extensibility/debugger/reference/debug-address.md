---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc25fb53db918486029e931a06a9e2de37f81c5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346307"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
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
El identificador de proceso.

`guidModule`\
El GUID del módulo que contiene esta dirección.

`tokClass`\
El token que identifica la clase o tipo de esta dirección.

> [!NOTE]
> Este valor es específico de un proveedor de símbolos y, por tanto, no tiene ningún significado general distinto como un identificador para un tipo de clase.

`addr`\
Un [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura que contiene una unión de estructuras que describen los tipos de direcciones individuales. El valor `addr`.`dwKind` procede de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración, que se explica cómo interpretar la unión.

## <a name="remarks"></a>Comentarios
Esta estructura se pasa a la [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método que deben rellenarse.

**Advertencia [C++ sólo]**

Si `addr.dwKind` es `ADDRESS_KIND_METADATA_LOCAL` y si `addr.addr.addrLocal.pLocal` no es un valor null, entonces debe llamar al método `Release` en el puntero de token:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
