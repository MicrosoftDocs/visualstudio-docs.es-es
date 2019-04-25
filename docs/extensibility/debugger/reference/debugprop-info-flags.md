---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 131e014e3714df708c5ef1526ecb911531c5a5c3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689114"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Especifica qué información se va a recuperar sobre un objeto de propiedad de depuración.

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

## <a name="members"></a>Miembros
DEBUGPROP_INFO_FULLNAME Initialize o usar el `bstrFullName` campo.

DEBUGPROP_INFO_NAME Initialize o usar el `bstrName` campo.

DEBUGPROP_INFO_TYPE Initialize o usar el `bstrType` campo.

DEBUGPROP_INFO_VALUE Initialize o usar el `bstrValue` campo.

DEBUGPROP_INFO_ATTRIB Initialize o usar el `dwAttrib` campo.

DEBUGPROP_INFO_PROP Initialize o usar el `pProperty` campo que contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz.

DEBUGPROP_INFO_VALUE_AUTOEXPAND especifica que el campo de valor debe contener el valor expandido automática, si está disponible para este tipo de objeto.

DEBUGPROP_INFO_VALUE_NOFUNCEVAL en desuso.

DEBUGPROP_INFO_VALUE_RAW no devuelven los valores beautified o miembros (es decir, no dan formato a los valores).

DEBUGPROP_INFO_VALUE_NO_TOSTRING no devuelven valores sintetizados especiales (por ejemplo, no llame a `ToString()` en un objeto para generar un valor).

DEBUGPROP_INFO_NONE especifica que no se establecen marcas.

DEBUGPROP_INFO_STANDARD Initialize o usar el `dwAttrib`, `bstrName`, `bstrType`, y `bstrValue` campos.

DEBUGPROP_INFO_All indica una máscara de todas las marcas.

## <a name="remarks"></a>Comentarios
Estos valores se pasan a la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), y [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) métodos para indicar cuáles son los campos que se inicialice la [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura.

Estos valores también se usan para la `dwFields` miembro de la `DEBUG_PROPERTY_INFO` estructura para indicar qué campos de la estructura se usan y válido cuando se devuelve la estructura.

Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
