---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54bb93fa6f88c02731691728bceacdd4a5fe2036
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694353"
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

## <a name="members"></a>Miembros
FIF_FUNCNAME Initialize o usar el `m_bstrFuncName` campo.

FIF_RETURNTYPE Initialize o usar el `m_bstrReturnType` campo.

FIF_ARGS Initialize o usar el `m_bstrArgs` campo.

FIF_LANGUAGE Initialize o usar el `m_bstrLanguage` campo.

FIF_MODULE Initialize o usar el `m_bstrModule` campo.

FIF_STACKRANGE Initialize o usar el `m_addrMin` y `m_addrMax` campos (intervalo de pila).

FIF_FRAME Initialize o usar el `m_pFrame` campo.

FIF_DEBUGINFO Initialize o usar el `m_fHasDebugInfo` campo.

FIF_STALECODE Initialize o usar el `m_fStaleCode` campo.

FIF_ANNOTATEDFRAME Initialize o usar el `m_fAnnotatedFrame` campo.

FIF_DEBUG_MODULEP Initialize o usar el `m_pModule` campo.

FIF_FUNCNAME_FORMAT formatos de nombre de la función. El resultado se devuelve en el `m_bstrFunName` campo y no hay otros campos se rellenan.

FIF_FUNCNAME_RETURNTYPE agrega el tipo de valor devuelto para la `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS agrega los argumentos para el `m_bstrFuncName` campo.

FIF_FUNCNAME_LANGUAGE agrega el idioma para el `m_bstrFuncName` campo.

FIF_FUNCNAME_MODULE agrega el nombre del módulo para el `m_bstrFuncName` campo.

FIF_FUNCNAME_LINES agrega el número de líneas para el `m_bstrFuncName` campo.

FIF_FUNCNAME_OFFSET agrega a la `m_bstrFuncName` campo el desplazamiento en bytes desde el principio de la línea si `FIF_FUNCNAME_LINES` se especifica. Si `FIF_FUNCNAME_LINES` no se especifica, o si los números de línea no están disponibles, agrega el desplazamiento en bytes desde el principio de la función.

FIF_FUNCNAME_ARGS_TYPES agrega el tipo de cada argumento de función para el `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_NAMES agrega el nombre de cada argumento de función para el `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_VALUES agrega el valor de cada argumento de función para el `m_bstrFuncName` campo.

FIF_FUNCNAME_ARGS_ALL agrega el tipo, nombre y valor de todos los argumentos de la `m_bstrFuncName` campo.

FIF_ARGS_TYPES los tipos de argumento se recupera y da formato.

FIF_ARGS_NAMES los nombres de argumento se recupera y da formato.

FIF_ARGS_VALUES los valores de argumento se recupera y da formato.

Recuperar FIF_ARGS_ALL y el tipo de formato, nombre y valor de todos los argumentos.

FIF_ARGS_NOFORMAT especifica que los argumentos no son tengan el formato (por ejemplo, no agregue apertura y cierre de la lista de argumentos entre paréntesis ni agregar un separador entre los argumentos).

FIF_ARGS_NO_FUNC_EVAL especifica que la evaluación (propiedad) de la función no debe usarse cuando se recuperan valores de argumento.

FIF_FILTER_NON_USER_CODE el motor de depuración es filtrar marcos de código de no usuario, por lo que no se incluyen.

FIF_ARGS_NO_TOSTRING no permiten `ToString()` función evaluación o cuando se devuelven los argumentos de la función de formato.

Información del marco FIF_DESIGN_TIME_EXPR_EVAL debe ser recibido del dominio de aplicación hospedado en lugar de con el proceso de hospedaje.

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
