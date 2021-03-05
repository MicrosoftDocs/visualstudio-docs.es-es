---
description: Especifica la información que se va a recuperar sobre una solicitud de punto de interrupción.
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f7ee5d8dbf48ad8d1b07512727b1b91635ab990
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162464"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Especifica la información que se va a recuperar sobre una solicitud de punto de interrupción.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>Campos
`BPREQI_BPLOCATION`\
Inicialice/use el `bpLocation` campo (ubicación del punto de interrupción) de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI_LANGUAGE`\
Inicialice o use el `guidLanguage` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_PROGRAM`\
Inicialice o use el `pProgram` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_PROGRAMNAME`\
Inicialice o use el `bstrProgramName` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_THREAD`\
Inicialice o use el `pThread` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_THREADNAME`\
Inicialice o use el `bstrThreadName` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_PASSCOUNT`\
Inicialice o use el `bpPassCount` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_CONDITION`\
Inicialice/use el `bpCondition` campo (condición de punto de interrupción) de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_FLAGS`\
Inicialice o use el `dwFlags` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI_ALLOLDFIELDS`\
Inicializar o utilizar todos los campos para el de la `BP_REQUEST_INFO` estructura.

`BPREQI_VENDOR`\
Inicializar/usar el `guidVendor` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI_CONSTRAINT`\
Inicializar/usar el `bstrConstraint` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI_TRACEPOINT`\
Inicializar/usar el `bstrTracepoint` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI_ALLFIELDS`\
Especifica todos los campos de la `BP_REQUEST_INFO2` estructura.

## <a name="remarks"></a>Observaciones
Se pasa como argumento a los métodos [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) y [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) para especificar los campos de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) que se van a inicializar.

Estas marcas también se usan para indicar los campos de las `BP_REQUEST_INFO` estructuras y que `BP_REQUEST_INFO2` se usan y son válidos cuando se devuelve cada estructura.

Estos valores se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
