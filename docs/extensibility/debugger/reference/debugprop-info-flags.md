---
description: Especifica qué información se va a recuperar sobre un objeto de propiedad de depuración.
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170528"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Especifica qué información se va a recuperar sobre un objeto de propiedad de depuración.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`DEBUGPROP_INFO_FULLNAME`\
Inicializar/usar el `bstrFullName` campo.

`DEBUGPROP_INFO_NAME`\
Inicializar/usar el `bstrName` campo.

`DEBUGPROP_INFO_TYPE`\
Inicializar/usar el `bstrType` campo.

`DEBUGPROP_INFO_VALUE`\
Inicializar/usar el `bstrValue` campo.

`DEBUGPROP_INFO_ATTRIB`\
Inicializar/usar el `dwAttrib` campo.

`DEBUGPROP_INFO_PROP`\
Inicialice o use el `pProperty` campo que contiene una interfaz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Especifica que el campo de valor debe contener el valor de expansión automática, si está disponible, para este tipo de objeto.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Desusado.

`DEBUGPROP_INFO_VALUE_RAW`\
No devuelva ningún valor o miembro de beautified (es decir, no formatee los valores).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
No devuelva ningún valor de sintetizado especial (por ejemplo, no llame a `ToString()` en un objeto para generar un valor).

`DEBUGPROP_INFO_NONE`\
Especifica que no hay marcas establecidas.

`DEBUGPROP_INFO_STANDARD`\
Inicialice o use los `dwAttrib` `bstrName` campos,, `bstrType` y `bstrValue` .

`DEBUGPROP_INFO_All`\
Indica una máscara de todas las marcas.

## <a name="remarks"></a>Observaciones
Estos valores se pasan a los métodos [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)y [EnumProperties (](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para indicar los campos que se van a inicializar en la estructura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

Estos valores también se usan para que el `dwFields` miembro de la `DEBUG_PROPERTY_INFO` estructura indique qué campos de la estructura se usan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
