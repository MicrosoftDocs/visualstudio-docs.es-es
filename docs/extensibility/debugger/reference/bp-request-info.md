---
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35a1202f4990f4f6370ad031c896ba85ebb6d816
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737894"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Contiene la información necesaria para implementar un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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
};
```

## <a name="members"></a>Miembros
`dwFields`\
Combinación de marcas de la enumeración [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica qué campos se rellenan.

`guidLanguage`\
GUID de lenguaje.

`bpLocation`\
Estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica el tipo de ubicación del punto de interrupción.

`pProgram`\
El objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa la aplicación en la que se produce el punto de interrupción.

`bstrProgramName`\
Nombre de la aplicación en la que se produce el punto de interrupción.

`pThread`\
El objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se produce el punto de interrupción.

`bstrThreadName`\
Nombre del subproceso en el que se produce el punto de interrupción.

`bpCondition`\
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estructura que describe las condiciones en las que se activará el punto de interrupción.

`bpPassCount`\
[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que contiene la información de recuento de pases del punto de interrupción.

`dwFlags`\
Combinación de marcas de la enumeración [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica las marcas del punto de interrupción solicitado.

## <a name="remarks"></a>Observaciones
El método [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) devuelve esta estructura.

Si necesita obtener el GUID del proveedor del motor de depuración, la restricción de punto de interrupción o el punto de seguimiento, vea la estructura [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
