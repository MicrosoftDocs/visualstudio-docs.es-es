---
description: Describe el recuento y las condiciones en las que se desencadena un punto de interrupción condicional.
title: BP_PASSCOUNT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c1e44ede0f39b3d1b33967311365508da6a701d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144161"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
Describe el recuento y las condiciones en las que se desencadena un punto de interrupción condicional.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_PASSCOUNT {
    DWORD              dwPassCount;
    BP_PASSCOUNT_STYLE stylePassCount;
} BP_PASSCOUNT;
```

```csharp
public struct BP_PASSCOUNT {
    public uint dwPassCount;
    public uint stylePassCount;
};
```

## <a name="members"></a>Members
`dwPassCount`\
Número de veces que se va a pasar el punto de interrupción antes de activarlo.

`stylePassCount`\
Un valor de la enumeración [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) que especifica el estilo del recuento de pasos de punto de interrupción.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) .

Esta estructura también se pasa como parámetro a los métodos[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) y[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)
- [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)
- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
