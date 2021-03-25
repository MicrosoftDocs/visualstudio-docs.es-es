---
description: Especifica las marcas que controlan la evaluación de expresiones.
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcf68b95bb905d41aaab906603cd4dd248e52ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095945"
---
# <a name="evalflags"></a>EVALFLAGS
Especifica las marcas que controlan la evaluación de expresiones.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Campos
`EVAL_RETURNVALUE`\
Especifica que se debe evaluar el valor devuelto, si existe.

`EVAL_NOSIDEEFFECTS`\
Especifica que no se permiten efectos secundarios.

`EVAL_ALLOWBPS`\
Especifica la detención en puntos de interrupción.

`EVAL_ALLOWERRORREPORT`\
Especifica el informe de errores para el host que se va a permitir. Se usa principalmente para la evaluación de expresiones en el script en Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Fuerza que las funciones se evalúen como direcciones, en lugar de invocar la función.

`EVAL_NOFUNCEVAL`\
Impide que se evalúe la función. Por ejemplo, considere el `int` token en la expresión `myExpression(int) + 10` . Esta función se puede evaluar correctamente como una dirección, pero no como un valor.

`EVAL_NOEVENTS`\
Marca para indicar que los eventos que se producen durante la evaluación de la expresión no se deben enviar al administrador de depuración de sesión (SDM) o al IDE.

## <a name="remarks"></a>Observaciones
Estas marcas se pasan como un argumento a los métodos [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) y [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .

Estas marcas se pueden combinar con una operación OR bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
