---
title: BP_REQUEST_INFO2 de la casa de la inser Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04d1db2ca8176678d8a72a84ede2bddcbfa2f152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737877"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Contiene la información necesaria para implementar un punto de interrupción, incluido el GUID del proveedor, la restricción y el punto de seguimiento.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Miembros
`dwFields`\
Una combinación de indicadores de la [enumeración BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica qué campos se rellenan.

`guidLanguage`\
GUID de lenguaje.

`bpLocation`\
La [estructura BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica el tipo de la ubicación del punto de interrupción.

`pProgram`\
El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa la aplicación en la que se produce el punto de interrupción.

`bstrProgramName`\
El nombre de la aplicación en la que se produce el punto de interrupción.

`pThread`\
El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce el punto de interrupción.

`bstrThreadName`\
El nombre del subproceso en el que se produce el punto de interrupción.

`bpCondition`\
La [estructura BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que describe las condiciones en las que se desencadenará el punto de interrupción.

`bpPassCount`\
La [estructura BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contiene la información de recuento de pasadas del punto de interrupción.

`dwFlags`\
Una combinación de indicadores de la [enumeración BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica los indicadores para el punto de interrupción solicitado.

`guidVendor`\
GUID del proveedor. Puede ser un valor nulo.

`bstrConstraint`\
Nombre de la restricción de punto de interrupción. Puede ser un valor nulo.

`bstrTracepoint`\
Nombre del punto de seguimiento. Puede ser un valor nulo.

## <a name="remarks"></a>Observaciones
Esta estructura es devuelta por el [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
