---
description: Especifica el estilo de condición del punto de interrupción para los puntos de interrupción pendientes y enlazados.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 611df036ff876e10096013070cac097bc51a8986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085421"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Especifica el estilo de condición del punto de interrupción para los puntos de interrupción pendientes y enlazados.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Campos
`BP_COND_NONE`\
Activa el punto de interrupción cuando se alcanza la posición del punto de interrupción. No se especificó ninguna condición de punto de interrupción.

`BP_COND_WHEN_TRUE`\
Activa el punto de interrupción solo cuando la expresión condicional asociada al punto de interrupción se evalúa como `true` .

`BP_COND_WHEN_CHANGED`\
Activa el punto de interrupción solo cuando el valor de la expresión condicional asociada al punto de interrupción ha cambiado respecto a su evaluación anterior.

## <a name="remarks"></a>Observaciones
Se utiliza para el `styleCondition` miembro de la estructura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
