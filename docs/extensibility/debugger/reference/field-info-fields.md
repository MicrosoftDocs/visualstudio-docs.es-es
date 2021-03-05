---
description: Especifica la información que se va a recuperar sobre un objeto IDebugField.
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170294"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Especifica la información que se va a recuperar sobre un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
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

## <a name="fields"></a>Campos
`FIF_FULLNAME`\
Inicialice o use el `bstrFullName` campo de la estructura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .

`FIF_NAME`\
Inicializar/usar el `bstrName` campo en la `FIELD_INFO` estructura.

`FIF_TYPE`\
Inicializar/usar el `bstrType` campo en la `FIELD_INFO` estructura.

`FIF_MODIFIERS`\
Inicializar/usar el `bstrModifiers` campo en la `FIELD_INFO` estructura.

## <a name="remarks"></a>Observaciones
Estos valores también se pasan como argumento al método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para especificar qué campos de la estructura de [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) se van a inicializar.

Estos valores también se usan en el `dwFields` miembro de la `FIELD_INFO` estructura para indicar qué campos se usan y son válidos.

Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: SH. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
