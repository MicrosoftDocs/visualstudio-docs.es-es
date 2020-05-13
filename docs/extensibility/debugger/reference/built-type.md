---
title: BUILT_TYPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737703"
---
# <a name="built_type"></a>BUILT_TYPE
Esta estructura especifica información sobre un tipo de campo tomado de metadatos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>Miembros
`ulAppDomainID`\
ID de la aplicación de la que procede el símbolo. Esto se utiliza para identificar de forma única una instancia de la aplicación.

`guidModule`\
Guid del módulo que contiene este campo.

`pUnderlyingField`\
Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que identifica el campo subyacente asociado a este campo compilado.

## <a name="remarks"></a>Observaciones
Esta estructura aparece como parte de la `dwKind` unión `TYPE_INFO` en la `TYPE_KIND_BUILT` [estructura TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando se establece el campo de la estructura en (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
