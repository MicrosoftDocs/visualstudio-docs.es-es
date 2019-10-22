---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 56990cf324c09764137b344f875322e80e613403
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350490"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Especifica la información para recuperar sobre un objeto de marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Campos
`FIF_FUNCNAME`\
Inicializar o usar el `m_bstrFuncName` campo.

`FIF_RETURNTYPE`\
Inicializar o usar el `m_bstrReturnType` campo.

`FIF_ARGS`\
Inicializar o usar el `m_bstrArgs` campo.

`FIF_LANGUAGE`\
Inicializar o usar el `m_bstrLanguage` campo.

`FIF_MODULE`\
Inicializar o usar el `m_bstrModule` campo.

`FIF_STACKRANGE`\
Inicializar o usar el `m_addrMin` y `m_addrMax` campos (intervalo de pila).

`FIF_FRAME`\
Inicializar o usar el `m_pFrame` campo.

`FIF_DEBUGINFO`\
Inicializar o usar el `m_fHasDebugInfo` campo.

`FIF_STALECODE`\
Inicializar o usar el `m_fStaleCode` campo.

`FIF_ANNOTATEDFRAME`\
Inicializar o usar el `m_fAnnotatedFrame` campo.

`FIF_DEBUG_MODULEP`\
Inicializar o usar el `m_pModule` campo.

`FIF_FUNCNAME_FORMAT`\
Formatos de nombre de la función. El resultado se devuelve en el `m_bstrFunName` campo y no hay otros campos se rellenan.

`FIF_FUNCNAME_RETURNTYPE`\
Agrega el tipo de valor devuelto para la `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS`\
Agrega los argumentos para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_LANGUAGE`\
El idioma que se agrega el `m_bstrFuncName` campo.

`FIF_FUNCNAME_MODULE`\
Agrega el nombre del módulo para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_LINES`\
Agrega el número de líneas para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_OFFSET`\
Agrega a la `m_bstrFuncName` campo el desplazamiento en bytes desde el principio de la línea si `FIF_FUNCNAME_LINES` se especifica. Si `FIF_FUNCNAME_LINES` no se especifica, o si los números de línea no están disponibles, agrega el desplazamiento en bytes desde el principio de la función.

`FIF_FUNCNAME_ARGS_TYPES`\
Agrega el tipo de cada argumento de función para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_NAMES`\
Agrega el nombre de cada argumento de función para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_VALUES`\
Agrega el valor de cada argumento de función para el `m_bstrFuncName` campo.

`FIF_FUNCNAME_ARGS_ALL`\
Agrega el tipo, nombre y valor de todos los argumentos de la `m_bstrFuncName` campo.

`FIF_ARGS_TYPES`\
Los tipos de argumento se recupera y da formato.

`FIF_ARGS_NAMES`\
Los nombres de argumento se recuperan y con formato.

`FIF_ARGS_VALUES`\
Los valores de argumento se recuperan y con formato.

`FIF_ARGS_ALL`\
Recuperar y dar formato el tipo, nombre y valor de todos los argumentos.

`FIF_ARGS_NOFORMAT`\
Especifica que los argumentos no se tiene el formato (por ejemplo, no agregue apertura y cierre de la lista de argumentos entre paréntesis ni agregar un separador entre los argumentos).

`FIF_ARGS_NO_FUNC_EVAL`\
Especifica que la evaluación de función (propiedad) no debe utilizarse cuando se recuperan valores de argumento.

`FIF_FILTER_NON_USER_CODE`\
El motor de depuración es filtrar marcos de código de no usuario, por lo que no se incluyen.

`FIF_ARGS_NO_TOSTRING`\
No permitir `ToString()` función evaluación o cuando se devuelven los argumentos de la función de formato.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Información del marco debe ser recibido desde el dominio de aplicación hospedado en lugar de con el proceso de hospedaje.

## <a name="remarks"></a>Comentarios
Estas marcas se pasan a la [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) y [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) métodos para indicar cuáles son los campos se inicialicen en la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) o más estructuras.

Estas marcas también se usan para indicar qué campos de la [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructura se usan y válido cuando se devuelve la estructura. Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
