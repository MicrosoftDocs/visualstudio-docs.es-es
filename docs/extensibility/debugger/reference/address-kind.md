---
title: ADDRESS_KIND de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738147"
---
# <a name="address_kind"></a>ADDRESS_KIND
Especifica los tipos de direcciones.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Fields
`ADDRESS_KIND_NATIVE`\
Una dirección nativa, representada por la estructura [NATIVE_ADDRESS.](../../../extensibility/debugger/reference/native-address.md)

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Una dirección no administrada `this` `Me` relativa a un (en Visual Basic) puntero y representado por el [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estructura.

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Una dirección física no administrada, representada por la estructura [UNMANAGED_ADDRESS_PHYSICAL.](../../../extensibility/debugger/reference/unmanaged-address-physical.md)

`ADDRESS_KIND_METHOD`\
Método de una clase, representado por la [estructura METADATA_ADDRESS_METHOD.](../../../extensibility/debugger/reference/metadata-address-method.md)

`ADDRESS_KIND_FIELD`\
Un campo de una clase, representado por la [estructura METADATA_ADDRESS_FIELD.](../../../extensibility/debugger/reference/metadata-address-field.md)

`ADDRESS_KIND_LOCAL`\
La dirección es para una variable local y está representada por la estructura [METADATA_ADDRESS_LOCAL.](../../../extensibility/debugger/reference/metadata-address-local.md)

`ADDRESS_KIND_PARAM`\
Un método o parámetro de función, representado por la [estructura METADATA_ADDRESS_PARAM.](../../../extensibility/debugger/reference/metadata-address-param.md)

`ADDRESS_KIND_ARRAYELEM`\
Un elemento de matriz, representado por la [estructura METADATA_ADDRESS_ARRAYELEM.](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)

`ADDRESS_KIND_RETVAL`\
Un valor devuelto, representado por la estructura [METADATA_ADDRESS_RETVAL.](../../../extensibility/debugger/reference/metadata-address-retval.md)

## <a name="remarks"></a>Observaciones
El [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método devuelve el [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que contiene una unión de posibles estructuras, la [estructura DEBUG_ADDRESS_UNION.](../../../extensibility/debugger/reference/debug-address-union.md) El `dwKind` campo `DEBUG_ADDRESS_UNION` de la `ADDRESS_KIND` estructura contiene el valor y describe cómo interpretar el campo de unión.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
