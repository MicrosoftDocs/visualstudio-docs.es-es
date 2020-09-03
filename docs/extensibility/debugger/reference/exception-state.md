---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736957"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Especifica el estado de excepción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Campos
`EXCEPTION_NONE`\
No se detenga en la excepción.

`EXCEPTION_STOP_FIRST_CHANCE`\
Detener en la primera activación de la excepción. Al describir un evento de excepción, esta marca indica que el evento de excepción es un evento de excepción de primera oportunidad.

`EXCEPTION_STOP_SECOND_CHANCE`\
Detener en la segunda activación de la excepción. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción de segunda oportunidad.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Detener en la primera activación de una excepción de modo de usuario. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción de usuario de primera oportunidad.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Detener cuando no se detecte una excepción de modo de usuario. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción de modo de usuario no capturado.

`EXCEPTION_STOP_ALL`\
Detenga en cualquier excepción. No se utiliza al describir un evento de excepción.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Al describir un evento de excepción, indica que no se puede continuar con la excepción.

`EXCEPTION_CODE_SUPPORTED`\
Indica que la excepción tiene código que lo admite. Se usa para mostrar una excepción

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica que el código de excepción se debe mostrar en formato hexadecimal. Se usa para mostrar una excepción.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica que el código de excepción admite JustMyCode. Se usa para mostrar una excepción.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica que el depurador de código administrado debe controlar las excepciones. Si no se establece, el depurador predeterminado controla las excepciones. Se pasa al método [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) y no se usa en la estructura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) .

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NO USAR.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NO USAR.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NO USAR.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NO USAR.

## <a name="remarks"></a>Observaciones
Se usa como `dwState` miembro de la estructura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) para indicar el estado de la excepción y lo que se puede hacer sobre ella.

Estos valores también se pasan al método [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) para establecer el estado de todas las excepciones.

Estas marcas se pueden combinar con una operación OR bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
