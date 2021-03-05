---
description: Especifica la condición asociada al recuento de pasos de punto de interrupción que hace que se active el punto de interrupción.
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e216b61d6fed41571baa7f68201d96f84532fc3a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144174"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Especifica la condición asociada al recuento de pasos de punto de interrupción que hace que se active el punto de interrupción.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`BP_PASSCOUNT_NONE`\
Especifica que no hay ningún estilo de número de pasadas de punto de interrupción.

`BP_PASSCOUNT_EQUAL`\
Establece el estilo de recuento de pasadas de punto de interrupción en Equal. El punto de interrupción se desencadena cuando el número de veces que se alcanza el punto de interrupción es igual al número de pasos.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Establece el estilo de recuento de pasadas de punto de interrupción en igual o mayor. El punto de interrupción se desencadena cuando el número de veces que se alcanza el punto de interrupción es igual o mayor que el número de pasos.

`BP_PASSCOUNT_MOD`\
Especifica un recuento de pases de módulo. Por ejemplo, si el recuento de pasos es del tipo `BP_PASSCOUNT_MOD` y el valor del recuento de pasos es 4, el punto de interrupción se desencadena cada vez que el número de llamadas es múltiplo de 4.

## <a name="remarks"></a>Observaciones
Se utiliza para el `stylePassCount` miembro de la estructura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que, a su vez, es miembro de las estructuras [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
