---
title: BPREQI_FIELDS90 de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737740"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera los valores válidos que especifican la información que se va a recuperar sobre una solicitud de punto de interrupción. Esta enumeración extiende la [enumeración BPREQI_FIELDS.](../../../extensibility/debugger/reference/bpreqi-fields.md)

## <a name="syntax"></a>Sintaxis

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

## <a name="fields"></a>Fields
`BPREQI90_BPLOCATION`\
Inicializar o `bpLocation` utilizar el campo (ubicación del punto de interrupción) de la [estructura BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI90_LANGUAGE`\
Inicializar o `guidLanguage` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_PROGRAM`\
Inicializar o `pProgram` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_PROGRAMNAME`\
Inicializar o `bstrProgramName` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_THREAD`\
Inicializar o `pThread` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_THREADNAME`\
Inicializar o `bstrThreadName` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_PASSCOUNT`\
Inicializar o `bpPassCount` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_CONDITION`\
Inicializar o `bpCondition` utilizar el campo (condición de punto de interrupción) de la `BP_REQUEST_INFO` estructura o. `BP_REQUEST_INFO2`

`BPREQI90_FLAGS`\
Inicializar o `dwFlags` utilizar el `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo de la estructura o.

`BPREQI90_ALLOLDFIELDS`\
Inicializar o utilizar todos los `BP_REQUEST_INFO` campos para la estructura.

`BPREQI90_VENDOR`\
Inicializar o `guidVendor` utilizar `BP_REQUEST_INFO2` el campo de estructura.

`BPREQI90_CONSTRAINT`\
Inicializar o `bstrConstraint` utilizar `BP_REQUEST_INFO2` el campo de estructura.

`BPREQI90_TRACEPOINT`\
Inicializar o `bstrTracepoint` utilizar `BP_REQUEST_INFO2` el campo de estructura.

`BPREQI90_MACROTRACEPOINT`\
Inicializar o `bstrMacroTracepoint` utilizar `BP_REQUEST_INFO2` el campo de estructura. BPREQI_ALLFIELDS no incluye este campo.

`BPREQI90_ALLFIELDS`\
Especifica todos los `BP_REQUEST_INFO2` campos de la estructura.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
