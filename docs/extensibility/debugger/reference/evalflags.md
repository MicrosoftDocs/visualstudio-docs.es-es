---
title: EVALFLAGS ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737112"
---
# <a name="evalflags"></a>EVALFLAGS
Especifica los indicadores que controlan la evaluación de expresiones.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EVALFLAGS {
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
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Fields
`EVAL_RETURNVALUE`\
Especifica que se evalúe el valor devuelto, si existe.

`EVAL_NOSIDEEFFECTS`\
Especifica que no se permiten efectos secundarios.

`EVAL_ALLOWBPS`\
Especifica la detención en puntos de interrupción.

`EVAL_ALLOWERRORREPORT`\
Especifica los informes de errores al host que se va a permitir. Se utiliza principalmente para la evaluación de expresiones en script en Internet Explorer.

`EVAL_FUNCTION_AS_ADDRESS`\
Fuerza las funciones que se evaluarán como direcciones, en lugar de invocar la función.

`EVAL_NOFUNCEVAL`\
Impide que se evalúe la función. Por ejemplo, `int` considere el `myExpression(int) + 10`token en la expresión . Esta función se puede evaluar correctamente como una dirección, pero no como un valor.

`EVAL_NOEVENTS`\
Marcar para indicar que los eventos que se producen durante la evaluación de expresiones no se deben enviar al administrador de depuración de sesión (SDM) o al IDE.

## <a name="remarks"></a>Observaciones
Estas marcas se pasan como argumento a los métodos [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) y [EvaluateSync.](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

Estas banderas pueden combinarse con un quiróctula bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
