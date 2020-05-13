---
title: BP_RESOLUTION_CODE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbfd16025d338b54bec8e2e4276de62c8d00477e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737850"
---
# <a name="bp_resolution_code"></a>BP_RESOLUTION_CODE
Describe la ubicación de un punto de interrupción de código.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_RESOLUTION_CODE {
    IDebugCodeContext2* pCodeContext;
} BP_RESOLUTION_CODE;
```

```csharp
public struct BP_RESOLUTION_CODE {
    public IDebugCodeContext2 pCodeContext;
};
```

## <a name="members"></a>Miembros
`pCodeContext`\
El [objeto IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que identifica la posición del punto de interrupción en el código.

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
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
