---
title: BP_FLAGS90 Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738049"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Enumera los valores válidos para las marcas opcionales. Las marcas opcionales se pueden utilizar para especificar información adicional al establecer un punto de interrupción. Esta enumeración extiende la [enumeración BP_FLAGS.](../../../extensibility/debugger/reference/bp-flags.md)

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Fields
`BP90_FLAG_NONE`\
No especifica ninguna marca de punto de interrupción.

`BP90_FLAG_MAP_DOCPOSITION`\
Especifica que el motor de depuración (DE) debe asignar el punto de interrupción mediante la posición del documento. Esto solo es aplicable a los puntos de interrupción establecidos en archivos de origen orientados a scripts, como Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Especifica que el motor de depuración debe procesar el punto de interrupción, pero que el motor de depuración no debe detenerse allí en última instancia; es decir, no se debe enviar un objeto de evento [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Esta marca está diseñada para usarse principalmente con puntos de seguimiento.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Utilizado por el motor de depuración nativo para determinar si se debe borrar el estado de paso a paso. Se diferencia de BP90_FLAG_DONT_STOP porque no se establece BP90_FLAG_DONT_STOP si el punto de seguimiento ejecuta una macro.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
