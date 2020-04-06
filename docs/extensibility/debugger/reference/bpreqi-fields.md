---
title: BPREQI_FIELDS de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737750"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Especifica la información que se va a recuperar sobre una solicitud de punto de interrupción.

## <a name="syntax"></a>Sintaxis

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

## <a name="fields"></a>Fields
`BPREQI_BPLOCATION`\
Inicializar/utilizar `bpLocation` el campo (ubicación del punto de interrupción) de la [estructura BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Inicializar/utilizar `guidLanguage` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_PROGRAM`\
Inicializar/utilizar `pProgram` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_PROGRAMNAME`\
Inicializar/utilizar `bstrProgramName` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_THREAD`\
Inicializar/utilizar `pThread` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_THREADNAME`\
Inicializar/utilizar `bstrThreadName` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_PASSCOUNT`\
Inicializar/utilizar `bpPassCount` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_CONDITION`\
Inicializar/utilizar `bpCondition` el campo (condición `BP_REQUEST_INFO` de `BP_REQUEST_INFO2` punto de interrupción) de la estructura o.

`BPREQI_FLAGS`\
Inicializar/utilizar `dwFlags` el campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de la estructura o.

`BPREQI_ALLOLDFIELDS`\
Inicializar/utilizar todos los campos `BP_REQUEST_INFO` para la estructura.

`BPREQI_VENDOR`\
Inicializar/utilizar `guidVendor` el `BP_REQUEST_INFO2` campo de estructura.

`BPREQI_CONSTRAINT`\
Inicializar/utilizar `bstrConstraint` el `BP_REQUEST_INFO2` campo de estructura.

`BPREQI_TRACEPOINT`\
Inicializar/utilizar `bstrTracepoint` el `BP_REQUEST_INFO2` campo de estructura.

`BPREQI_ALLFIELDS`\
Especifica todos los `BP_REQUEST_INFO2` campos de la estructura.

## <a name="remarks"></a>Observaciones
Se pasa como argumento a los métodos [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) y [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) para especificar qué campos de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) se van a inicializar.

Estas marcas también se utilizan para `BP_REQUEST_INFO` `BP_REQUEST_INFO2` indicar qué campos de las estructuras y se utilizan y son válidos cuando se devuelve cada estructura.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
