---
description: Describe el resultado de enlazar un punto de interrupción de datos.
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 848a2b22ece8d3a51d7eef28b1f8baa7164ca22d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054717"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Describe el resultado de enlazar un punto de interrupción de datos.

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
Expresión de datos que se ha enlazado.

`bstrFunc`\
Nombre de la función en la que está enlazado el punto de interrupción de datos (si existe).

`bstrImage`\
Nombre del módulo (MyModule.dll, por ejemplo) en el que está enlazado el punto de interrupción de datos.

`dwFlags`\
Un valor de la enumeración [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , que describe cómo se implementa el punto de interrupción de datos.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , que, a su vez, es miembro de la estructura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devuelta por el método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
