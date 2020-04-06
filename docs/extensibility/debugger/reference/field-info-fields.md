---
title: FIELD_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736907"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Especifica qué información se va a recuperar acerca de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Fields
`FIF_FULLNAME`\
Inicializar/utilizar `bstrFullName` el campo en la estructura [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Inicializar/utilizar `bstrName` el campo `FIELD_INFO` de la estructura.

`FIF_TYPE`\
Inicializar/utilizar `bstrType` el campo `FIELD_INFO` de la estructura.

`FIF_MODIFIERS`\
Inicializar/utilizar `bstrModifiers` el campo `FIELD_INFO` de la estructura.

## <a name="remarks"></a>Observaciones
Estos valores también se pasan como argumento al método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para especificar qué campos de la estructura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) se van a inicializar.

Estos valores también se `dwFields` utilizan `FIELD_INFO` en el miembro de la estructura para indicar qué campos se utilizan y son válidos.

Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
