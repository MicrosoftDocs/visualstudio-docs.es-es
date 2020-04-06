---
title: DEBUGPROP_INFO_FLAGS de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737394"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Especifica qué información se va a recuperar acerca de un objeto de propiedad de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Fields
`DEBUGPROP_INFO_FULLNAME`\
Inicializar/utilizar `bstrFullName` el campo.

`DEBUGPROP_INFO_NAME`\
Inicializar/utilizar `bstrName` el campo.

`DEBUGPROP_INFO_TYPE`\
Inicializar/utilizar `bstrType` el campo.

`DEBUGPROP_INFO_VALUE`\
Inicializar/utilizar `bstrValue` el campo.

`DEBUGPROP_INFO_ATTRIB`\
Inicializar/utilizar `dwAttrib` el campo.

`DEBUGPROP_INFO_PROP`\
Inicializar o `pProperty` usar el campo que contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Especifica que el campo value debe contener el valor expandido automáticamente, si está disponible, para este tipo de objeto.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
En desuso.

`DEBUGPROP_INFO_VALUE_RAW`\
No devuelva ningún valor o miembro embellecido (es decir, no dé formato a los valores).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
No devuelva ningún valor sintetizado especial (por ejemplo, no llame `ToString()` a un objeto para producir un valor).

`DEBUGPROP_INFO_NONE`\
Especifica que no hay marcas establecidas.

`DEBUGPROP_INFO_STANDARD`\
Inicializar/utilizar `dwAttrib`los `bstrName` `bstrType`campos `bstrValue` , , , y .

`DEBUGPROP_INFO_All`\
Indica una máscara de todas las marcas.

## <a name="remarks"></a>Observaciones
Estos valores se pasan a los métodos [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)y [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para indicar qué campos se van a inicializar la estructura [DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

Estos valores también se `dwFields` utilizan `DEBUG_PROPERTY_INFO` para el miembro de la estructura para indicar qué campos de la estructura se utilizan y válidos cuando se devuelve la estructura.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
