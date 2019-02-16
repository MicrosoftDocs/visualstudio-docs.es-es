---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a02eb1407bf9645fd8a1ff3f56c971a24a94417d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318204"
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
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
`dwFields`  
Una colección de marcas de la [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) enumeraciones que especifica qué campos se rellenan.

`bpResLocation`  
El [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) estructura que especifica la ubicación del punto de interrupción en código o datos.

`pProgram`  
El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa la aplicación en el que se produjo el error de punto de interrupción.

`pThread`  
El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se ejecuta la aplicación que contiene el error de punto de interrupción.

## <a name="remarks"></a>Comentarios
Esta estructura es devuelto por [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md).

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)  
[BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)  
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
