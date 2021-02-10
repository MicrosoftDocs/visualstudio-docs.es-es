---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 073dac8de37edddc1b748c52258047cd2d85e218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937080"
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

## <a name="remarks"></a>Notas
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
