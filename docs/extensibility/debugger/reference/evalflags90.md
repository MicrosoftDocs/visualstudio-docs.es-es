---
description: Enumera los valores válidos para las marcas que controlan la evaluación de expresiones.
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e75b938f45df5d4fa91bec4b59964dfc6a54e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095932"
---
# <a name="evalflags90"></a>EVALFLAGS90
Enumera los valores válidos para las marcas que controlan la evaluación de expresiones. Esta enumeración extiende la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Campos
`EVAL90_RETURNVALUE`\
Especifica que se debe evaluar el valor devuelto, si existe.

`EVAL90_NOSIDEEFFECTS`\
Especifica que no se permiten efectos secundarios.

`EVAL90_ALLOWBPS`\
Especifica la detención en puntos de interrupción.

`EVAL90_ALLOWERRORREPORT`\
Especifica que se va a permitir el informe de errores en el host. Se usa principalmente para la evaluación de expresiones en el script en Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Fuerza que las funciones se evalúen como direcciones, en lugar de invocar la función.

`EVAL90_NOFUNCEVAL`\
Impide que se evalúe la función. Por ejemplo, considere el `int` token en la expresión `myExpression(int) + 10` . Esta función se puede evaluar correctamente como una dirección, pero no como un valor.

`EVAL90_NOEVENTS`\
Marca para indicar que los eventos que se producen durante la evaluación de la expresión no se deben enviar al administrador de depuración de sesión (SDM) o al IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Habilita la evaluación de expresiones en tiempo de diseño.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Permite la creación de variables implícitas.

`EVAL90_FORCE_EVALUATION_NOW`\
Fuerza la evaluación para que se produzca inmediatamente. Esto resulta útil cuando se atiende una solicitud, como una solicitud de usuario.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg90. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
