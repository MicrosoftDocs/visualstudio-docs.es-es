---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65393f6e162cb15ded7a0e598e360c7ce90bb3cd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717668"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Proporciona la razón que no está enlazado a un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="members"></a>Miembros
BPUR_UNKNOWN el motivo es desconocido.

BPUR_CODE_UNLOADED el código que contiene el punto de interrupción se ha descargado.

Se han vuelto a enlazar BPUR_BREAKPOINT_REBIND el punto de interrupción en una ubicación diferente. Esto puede ocurrir después de editar y continuar con las operaciones cuando se mueve el punto de interrupción o cuando el punto de interrupción se enlaza a un archivo con una ruta de acceso que ya no es válido.

BPUR_ BREAKPOINT_ERROR el punto de interrupción se determina como error después de que está enlazado. Esto sucede a los puntos de interrupción administrados cuyas condiciones ya no son válidos.

## <a name="remarks"></a>Comentarios
Devuelto por la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
