---
description: Esta estructura describe una variable, un parámetro o un campo local.
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47b7c7cb3a77d0ad925b044130901dd481b99943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162438"
---
# <a name="field_info"></a>FIELD_INFO
Esta estructura describe una variable, un parámetro o un campo local.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Members
`dwFields`\
Combinación de marcas de la enumeración [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) que especifica los miembros que se rellenan.

`bstrFullName`\
Nombre completo del campo.

`bstrName`\
Nombre corto del campo.

`bstrType`\
Tipo del campo.

`dwModifiers`\
Combinación de marcas de la enumeración [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) que describe el campo.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa al método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) en el que se rellena.

## <a name="requirements"></a>Requisitos
Encabezado: SH. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
