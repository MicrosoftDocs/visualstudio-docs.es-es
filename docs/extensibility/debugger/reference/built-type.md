---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35ae5661127c0e19e87c96a47a2985161beae7c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874387"
---
# <a name="built_type"></a>BUILT_TYPE
Esta estructura especifica información sobre un tipo de campo tomado de los metadatos.

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

## <a name="members"></a>Members
`ulAppDomainID`\
IDENTIFICADOR de la aplicación de la que procede el símbolo. Se utiliza para identificar de forma única una instancia de la aplicación.

`guidModule`\
GUID del módulo que contiene este campo.

`pUnderlyingField`\
Un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que identifica el campo subyacente asociado a este campo compilado.

## <a name="remarks"></a>Notas
Esta estructura aparece como parte de la Unión en la estructura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando el `dwKind` campo de la `TYPE_INFO` estructura se establece en `TYPE_KIND_BUILT` (un valor de la enumeración [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Requisitos
Encabezado: SH. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
