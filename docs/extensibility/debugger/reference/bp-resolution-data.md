---
title: BP_RESOLUTION_DATA Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737841"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Describe el resultado del enlace de un punto de interrupción de datos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Miembros
`bstrDataExpr`\
La expresión de datos que se ha enlazado.

`bstrFunc`\
El nombre de la función en la que se ha enlazado el punto de interrupción de datos (si existe).

`bstrImage`\
El nombre del módulo (MyModule.dll, por ejemplo) en el que se ha enlazado el punto de interrupción de datos.

`dwFlags`\
Valor de la [enumeración BP_RES_DATA_FLAGS,](../../../extensibility/debugger/reference/bp-res-data-flags.md) que describe cómo se implementa el punto de interrupción de datos.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) estructura, que es a su vez un miembro de la [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura devuelta por el [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
