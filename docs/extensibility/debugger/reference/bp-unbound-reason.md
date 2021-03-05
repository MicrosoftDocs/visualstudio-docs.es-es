---
description: Proporciona la razón por la que se desenlaza un punto de interrupción.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 857f07e70809200567b6c2f79c5a22aff78b4af8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162555"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Proporciona la razón por la que se desenlaza un punto de interrupción.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`BPUR_UNKNOWN`\
La razón es desconocida.

`BPUR_CODE_UNLOADED`\
Se ha descargado el código que contiene el punto de interrupción.

`BPUR_BREAKPOINT_REBIND`\
El punto de interrupción se ha reenlazado a una ubicación diferente. Esto puede ocurrir después de las operaciones de editar y continuar cuando se mueve el punto de interrupción, o cuando el punto de interrupción se enlaza a un archivo con una ruta de acceso que ya no es válida.

`BPUR_ BREAKPOINT_ERROR`\
El punto de interrupción se determina como erróneo una vez enlazado. Esto sucede con los puntos de interrupción administrados cuyas condiciones ya no son válidas.

## <a name="remarks"></a>Observaciones
Devuelto por el método [GetReason (](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
