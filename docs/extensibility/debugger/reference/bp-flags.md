---
title: BP_FLAGS de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738062"
---
# <a name="bp_flags"></a>BP_FLAGS
Proporciona indicadores opcionales que se pueden usar para especificar información adicional al establecer un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Fields
`BP_FLAG_NONE`\
No especifica ninguna marca de punto de interrupción.

`BP_FLAG_MAP_DOCPOSITION`\
Especifica que el motor de depuración (DE) debe asignar el punto de interrupción mediante la posición del documento. Esto solo es aplicable a los puntos de interrupción establecidos en archivos de origen orientados a scripts, como Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Especifica que el motor de depuración debe procesar el punto de interrupción, pero que el motor de depuración no debe detenerse allí (es decir, no se debe enviar un objeto de evento [IDebugBreakpointEvent2).](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Esta marca está diseñada para usarse principalmente con puntos de seguimiento.

## <a name="remarks"></a>Observaciones
Se utiliza `dwFlags` para el miembro de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
