---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352e4bdf6c79dc67f0bf396cb1164e96e80fbf5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337700"
---
# <a name="fieldinfo"></a>FIELD_INFO
Esta estructura describe otro campo, parámetro o una variable local.

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

## <a name="members"></a>Miembros
`dwFields`\
Una combinación de marcas de la [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeración que especifica qué miembros se rellenan.

`bstrFullName`\
El nombre completo del campo.

`bstrName`\
El nombre corto del campo.

`bstrType`\
El tipo del campo.

`dwModifiers`\
Una combinación de marcas de la [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeración que describe el campo.

## <a name="remarks"></a>Comentarios
Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método donde se rellena.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
