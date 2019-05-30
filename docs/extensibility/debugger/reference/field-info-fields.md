---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01853df78bfe731ea4b7159f7b3ebe352f3c5eaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337677"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Especifica qué información se va a recuperar sobre un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.

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

## <a name="fields"></a>Campos
`FIF_FULLNAME`\
Inicializar o usar el `bstrFullName` campo el [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura.

`FIF_NAME`\
Inicializar o usar el `bstrName` campo el `FIELD_INFO` estructura.

`FIF_TYPE`\
Inicializar o usar el `bstrType` campo el `FIELD_INFO` estructura.

`FIF_MODIFIERS`\
Inicializar o usar el `bstrModifiers` campo el `FIELD_INFO` estructura.

## <a name="remarks"></a>Comentarios
Estos valores también se pasan como argumento a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para especificar qué campos de la [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estructura deben inicializarse.

Estos valores también se usan en el `dwFields` miembro de la `FIELD_INFO` estructura para indicar qué campos se usan y válido.

Estas marcas se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
