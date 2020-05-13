---
title: BP_UNBOUND_REASON Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737771"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Proporciona la razón por la que un punto de interrupción no estaba enlazado.

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

## <a name="fields"></a>Fields
`BPUR_UNKNOWN`\
La razón es desconocida.

`BPUR_CODE_UNLOADED`\
El código que contiene el punto de interrupción se ha descargado.

`BPUR_BREAKPOINT_REBIND`\
El punto de interrupción se ha rebotado en una ubicación diferente. Esto puede suceder después de las operaciones Editar y Continuar cuando se mueve el punto de interrupción, o cuando el punto de interrupción está enlazado a un archivo con una ruta de acceso que ya no es válida.

`BPUR_ BREAKPOINT_ERROR`\
Se determina que el punto de interrupción es erróneo después de enlazarlo. Esto sucede con puntos de interrupción administrados cuyas condiciones ya no son válidas.

## <a name="remarks"></a>Observaciones
Devuelta por el [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
