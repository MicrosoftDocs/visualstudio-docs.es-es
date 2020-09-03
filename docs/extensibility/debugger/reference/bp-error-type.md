---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738071"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Especifica el tipo de error de un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Campos
`BPET_NONE`\
No especifica ningún error de punto de interrupción.

`BPET_TYPE_WARNING`\
Especifica un error de punto de interrupción de estilo de advertencia.

`BPET_TYPE_ERROR`\
Especifica un error de punto de interrupción de estilo de error.

`BPET_SEV_HIGH`\
Especifica un error de punto de interrupción de gravedad alta.

`BPET_SEV_GENERAL`\
Especifica un error de punto de interrupción de gravedad media.

`BPET_SEV_LOW`\
Especifica un error de punto de interrupción de gravedad baja.

`BPET_TYPE_MASK`\
Especifica un error de punto de interrupción de estilo de máscara.

`BPET_SEV_MASK`\
Especifica un error de punto de interrupción de estilo de máscara de gravedad.

`BPET_GENERAL_WARNING`\
Especifica un error de punto de interrupción de estilo general.

`BPET_GENERAL_ERROR`\
Especifica un error de punto de interrupción de estilo de error general.

`BPET_ALL`\
Especifica todos los tipos de error de punto de interrupción.

## <a name="remarks"></a>Observaciones
Estos valores se pueden combinar con una operación bit a bit `OR` y utilizarse para el `dwType` miembro de la estructura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) . Se pasa como un parámetro al método [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .

Un tipo de error de punto de interrupción se compone de un tipo y una gravedad. Esto significa que un tipo de error de punto de interrupción nunca es simplemente un tipo (por ejemplo, `BPET_TYPE_ERROR` ,) o una gravedad (por ejemplo, `BPET_SEV_GENERAL` ) por sí solo. `BPET_GENERAL_WARNING` y `BPET_GENERAL_ERROR` proporcionan valores predefinidos para los puntos de interrupción generales de advertencia y error.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
