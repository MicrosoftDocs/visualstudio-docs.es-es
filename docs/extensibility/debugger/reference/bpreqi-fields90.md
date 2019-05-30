---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f4d6df181ac15746202ae9f67e7b8874848e8f3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350543"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Enumera los valores válidos que especifican la información que se va a recuperar sobre una solicitud de punto de interrupción. Esta enumeración se extiende el [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeración.

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

## <a name="fields"></a>Campos
`BPREQI90_BPLOCATION`\
Inicializar o utilizar el `bpLocation` campo (ubicación de punto de interrupción) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructura.

`BPREQI90_LANGUAGE`\
Inicializar o utilizar el `guidLanguage` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_PROGRAM`\
Inicializar o utilizar el `pProgram` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_PROGRAMNAME`\
Inicializar o utilizar el `bstrProgramName` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_THREAD`\
Inicializar o utilizar el `pThread` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_THREADNAME`\
Inicializar o utilizar el `bstrThreadName` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_PASSCOUNT`\
Inicializar o utilizar el `bpPassCount` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_CONDITION`\
Inicializar o utilizar el `bpCondition` campo (condición de punto de interrupción) de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_FLAGS`\
Inicializar o utilizar el `dwFlags` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.

`BPREQI90_ALLOLDFIELDS`\
Inicializar o usar todos los campos de la de la `BP_REQUEST_INFO` estructura.

`BPREQI90_VENDOR`\
Inicializar o utilizar el `guidVendor` campo `BP_REQUEST_INFO2` estructura.

`BPREQI90_CONSTRAINT`\
Inicializar o utilizar el `bstrConstraint` campo `BP_REQUEST_INFO2` estructura.

`BPREQI90_TRACEPOINT`\
Inicializar o utilizar el `bstrTracepoint` campo `BP_REQUEST_INFO2` estructura.

`BPREQI90_MACROTRACEPOINT`\
Inicializar o utilizar el `bstrMacroTracepoint` campo `BP_REQUEST_INFO2` estructura. BPREQI_ALLFIELDS no incluye este campo.

`BPREQI90_ALLFIELDS`\
Especifica todos los campos de la `BP_REQUEST_INFO2` estructura.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
