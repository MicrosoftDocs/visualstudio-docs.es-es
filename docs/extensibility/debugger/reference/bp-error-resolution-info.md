---
title: BP_ERROR_RESOLUTION_INFO de la casa de la inser Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738087"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Describe la resolución de un punto de interrupción de error, incluida la ubicación, el programa y el subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Miembros
`dwFields`\
Una combinación de valores de la [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) enumeración especificando qué campos de esta estructura se rellenan.

`bpResLocation`\
El [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) unión, que especifica la ubicación de resolución de punto de interrupción.

`pProgram`\
El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa la aplicación en la que se produjo el error de punto de interrupción.

`pThread`\
El [objeto IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se ejecuta el error de punto de interrupción de la aplicación que generó el error de punto de interrupción.

`bstrMessage`\
Cadena que contiene cualquier mensaje de advertencia o error resultante de esta resolución de error.

`dwType`\
Valor de la [enumeración BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) que especifica el tipo de error de punto de interrupción.

## <a name="remarks"></a>Observaciones
Esta estructura se devuelve desde el [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
