---
title: DEBUGREF_INFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737390"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Especifica qué información se va a recuperar sobre un objeto de referencia de depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Fields
`DEBUGREF_INFO_NAME`\
Inicializar/utilizar `bstrName` el campo de la estructura.

`DEBUGREF_INFO_TYPE`\
Inicializar/utilizar `bstrType` el campo de la estructura.

`DEBUGREF_INFO_VALUE`\
Inicializar/utilizar `bstrValue` el campo de la estructura.

`DEBUGREF_INFO_ATTRIB`\
Inicializar/utilizar `dwAttrib` el campo de la estructura.

`DEBUGREF_INFO_REFTYPE`\
Inicializar/utilizar `dwRefType` el campo de la estructura.

`DEBUGREF_INFO_REF`\
Inicializar/utilizar `pReference` el campo de la estructura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
El campo value debe contener el valor expandido automáticamente, si está disponible, para este tipo de objeto.

`DEBUGREF_INFO_NONE`\
Indica que no se ha establecido ninguna marca.

`DEBUGREF_INFO_ALL`\
Indica una máscara de las marcas.

## <a name="remarks"></a>Observaciones
Estos indicadores se pasan a los métodos [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) y [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) para indicar qué campos de la estructura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) se van a inicializar.

Se utiliza `dwFields` para `DEBUG_REFERENCE_INFO` el miembro de la estructura para indicar qué campos se utilizan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
