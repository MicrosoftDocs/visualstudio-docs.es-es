---
title: dwTYPE_KIND de la casa de la inser Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737196"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Especifica cómo interpretar el tipo de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Fields
`TYPE_KIND_METADATA`\
La [unión TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) debe interpretarse como una estructura [METADATA_TYPE.](../../../extensibility/debugger/reference/metadata-type.md)

`TYPE_KIND_PDB`\
La `TYPE_INFO` unión debe interpretarse como una estructura [PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
La `TYPE_INFO` unión debe interpretarse como una estructura [BUILT_TYPE.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Observaciones
Los valores de esta `dwKind` enumeración aparecen en el campo de `type` la estructura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) y se usan para determinar cómo interpretar el miembro de unión. La `TYPE_INFO` estructura se devuelve mediante una llamada a la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
