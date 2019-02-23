---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71888e4e0b339b9b9b94946e8d9c49f8ffb1f84c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696825"
---
# <a name="addresskind"></a>ADDRESS_KIND
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

## <a name="terms"></a>Términos
Direcciones nativa de un ADDRESS_KIND_NATIVE, representado por la [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) estructura.

ADDRESS_KIND_UNMANAGED_THIS_RELATIVE una dirección no administrada respecto a un `this` (`Me` en Visual Basic) puntero y representado por la [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estructura.

ADDRESS_KIND_UNMANAGED_PHYSICAL una dirección física no administrada, representado por la [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) estructura.

Método ADDRESS_KIND_METHOD A una clase, representada por la [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) estructura.

Campo de un ADDRESS_KIND_FIELD de una clase, representada por la [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) estructura.

ADDRESS_KIND_LOCAL la dirección es una variable local y se representa mediante el [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) estructura.

ADDRESS_KIND_PARAM un método o función de parámetro, representado por la [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) estructura.

ADDRESS_KIND_ARRAYELEM un elemento de matriz, representado por la [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) estructura.

Valor de retorno de un ADDRESS_KIND_RETVAL, representado por la [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) estructura.

## <a name="remarks"></a>Comentarios
El [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método devuelve el [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que contiene una unión de las posibles estructuras, la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura. El `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura contiene el `ADDRESS_KIND` de valor y se describe cómo interpretar el campo union.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
