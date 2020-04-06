---
title: BP_PASSCOUNT_STYLE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737919"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Especifica la condición asociada con el recuento de pasadas de punto de interrupción que hace que se active el punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Fields
`BP_PASSCOUNT_NONE`\
No especifica ningún estilo de recuento de pasadas de punto de interrupción.

`BP_PASSCOUNT_EQUAL`\
Establece el estilo de recuento de pasadas de punto de interrupción en igual. El punto de interrupción se activa cuando el número de veces que se alcanza el punto de interrupción es igual al recuento de pasadas.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Establece el estilo de recuento de pasadas de punto de interrupción en igual o mayor. El punto de interrupción se activa cuando el número de veces que se alcanza el punto de interrupción es igual o mayor que el recuento de pasadas.

`BP_PASSCOUNT_MOD`\
Especifica un recuento de pasadas de módulo. Por ejemplo, si el recuento `BP_PASSCOUNT_MOD` de pasadas es del tipo y el valor del recuento de pasadas es 4, el punto de interrupción se activa cada vez que el recuento de aciertos es un múltiplo de 4.

## <a name="remarks"></a>Observaciones
Se utiliza `stylePassCount` para el miembro de la estructura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que a su vez es un miembro de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
