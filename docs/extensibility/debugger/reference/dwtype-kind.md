---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a33bdf1875426898a6db72831bee4d1d7ac1f9a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689257"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
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

#### <a name="parameters"></a>Parámetros
TYPE_KIND_METADATA el [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union debe interpretarse como un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estructura.

TYPE_KIND_PDB el `TYPE_INFO` union debe interpretarse como un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estructura.

TYPE_KIND_BUILT el `TYPE_INFO` union debe interpretarse como un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estructura.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración aparecen en la `dwKind` campo de la [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructurar y se usan para determinar cómo interpretar la `type` miembro de unión. El `TYPE_INFO` estructura devuelto por una llamada a la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
