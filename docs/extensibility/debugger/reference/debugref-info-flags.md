---
description: Especifica qué información se va a recuperar sobre un objeto de referencia de depuración.
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913490588fcf739e9659318cb72a9ca74d6db99d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096231"
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

## <a name="fields"></a>Campos
`DEBUGREF_INFO_NAME`\
Inicializar/usar el `bstrName` campo en la estructura.

`DEBUGREF_INFO_TYPE`\
Inicializar/usar el `bstrType` campo en la estructura.

`DEBUGREF_INFO_VALUE`\
Inicializar/usar el `bstrValue` campo en la estructura.

`DEBUGREF_INFO_ATTRIB`\
Inicializar/usar el `dwAttrib` campo en la estructura.

`DEBUGREF_INFO_REFTYPE`\
Inicializar/usar el `dwRefType` campo en la estructura.

`DEBUGREF_INFO_REF`\
Inicializar/usar el `pReference` campo en la estructura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
El campo de valor debe contener el valor de expansión automática, si está disponible, para este tipo de objeto.

`DEBUGREF_INFO_NONE`\
Indica que no se ha establecido ninguna marca.

`DEBUGREF_INFO_ALL`\
Indica una máscara de las marcas.

## <a name="remarks"></a>Observaciones
Estas marcas se pasan a los métodos [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) y [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) para indicar qué campos de la estructura de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) se van a inicializar.

Se utiliza para que el `dwFields` miembro de la `DEBUG_REFERENCE_INFO` estructura indique qué campos se usan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
