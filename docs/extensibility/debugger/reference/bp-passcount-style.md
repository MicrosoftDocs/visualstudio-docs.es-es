---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 809c63fe536166efe0779cd4e4dc0149b219390a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686059"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Especifica la condición asociada con el número de pase de punto de interrupción que hace que el punto de interrupción se activan.

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

## <a name="members"></a>Miembros
BP_PASSCOUNT_NONE se especifica ningún estilo de recuento de pase de punto de interrupción.

BP_PASSCOUNT_EQUAL establece el estilo de recuento de pase de punto de interrupción en el mismo. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual que el contador de pasos.

BP_PASSCOUNT_EQUAL_OR_GREATER establece el estilo de recuento de pase de punto de interrupción en igual o mayor. El punto de interrupción se desencadena cuando el número de veces que se visita el punto de interrupción es igual o mayor que el recuento de pass.

BP_PASSCOUNT_MOD especifica un módulo de recuento de pasos. Por ejemplo, si el contador de pasos es del tipo `BP_PASSCOUNT_MOD` y el valor de recuento de pass es 4, se activa el punto de interrupción cada vez que el recuento de visitas sea un múltiplo de 4.

## <a name="remarks"></a>Comentarios
Utilizado para la `stylePassCount` miembro de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que a su vez es miembro de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructuras.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
