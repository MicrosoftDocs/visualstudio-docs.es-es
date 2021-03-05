---
description: Enumera los valores válidos que especifican la información que se va a recuperar sobre una solicitud de punto de interrupción.
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5405f728cf979738de5a830421c4306c5e398bb2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151089"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera los valores válidos que especifican la información que se va a recuperar sobre una solicitud de punto de interrupción. Esta enumeración extiende la enumeración de [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Campos
`BPREQI90_BPLOCATION`\
Inicialice o use el `bpLocation` campo (ubicación del punto de interrupción) de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

`BPREQI90_LANGUAGE`\
Inicialice o use el `guidLanguage` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_PROGRAM`\
Inicialice o use el `pProgram` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_PROGRAMNAME`\
Inicialice o use el `bstrProgramName` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_THREAD`\
Inicialice o use el `pThread` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_THREADNAME`\
Inicialice o use el `bstrThreadName` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_PASSCOUNT`\
Inicialice o use el `bpPassCount` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_CONDITION`\
Inicialice o use el `bpCondition` campo (condición de punto de interrupción) de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_FLAGS`\
Inicialice o use el `dwFlags` campo de la `BP_REQUEST_INFO` `BP_REQUEST_INFO2` estructura o.

`BPREQI90_ALLOLDFIELDS`\
Inicializar o utilizar todos los campos para el de la `BP_REQUEST_INFO` estructura.

`BPREQI90_VENDOR`\
Inicialice o use el `guidVendor` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI90_CONSTRAINT`\
Inicialice o use el `bstrConstraint` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI90_TRACEPOINT`\
Inicialice o use el `bstrTracepoint` campo de la `BP_REQUEST_INFO2` estructura.

`BPREQI90_MACROTRACEPOINT`\
Inicialice o use el `bstrMacroTracepoint` campo de la `BP_REQUEST_INFO2` estructura. BPREQI_ALLFIELDS no incluye este campo.

`BPREQI90_ALLFIELDS`\
Especifica todos los campos de la `BP_REQUEST_INFO2` estructura.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
