---
title: BP_RESOLUTION_INFO de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70e66a936ec1eaf1f818ad249aa4eb14b0b63749
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737829"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
Describe la información de punto de interrupción enlazado para un punto de interrupción de código o un punto de interrupción de datos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>Miembros
`dwFields`\
Colección de indicadores de la [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) enumeraciones que especifica qué campos se rellenan.

`bpResLocation`\
La [estructura BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) que especifica la ubicación del punto de interrupción en el código o los datos.

`pProgram`\
El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa la aplicación en la que se produjo el error de punto de interrupción.

`pThread`\
El [objeto IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se ejecuta la aplicación que contiene el error de punto de interrupción.

## <a name="remarks"></a>Observaciones
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)devuelve esta estructura.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
