---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f05596b12151b3a40b87c6fc2f15659a38e3431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337688"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
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
Se detiene en la primera activación de la excepción. Al describir un evento de excepción, esta marca indica que el evento de excepción es un evento de excepción de primera oportunidad.

`EXCEPTION_STOP_SECOND_CHANCE`\
Se detiene en la segunda activación de la excepción. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción de la segunda oportunidad.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Se detiene en la primera activación de una excepción de modo de usuario. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción de usuario de primera oportunidad.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Deténgase cuando no se detecta una excepción de modo de usuario. Al describir un evento de excepción, indica que el evento de excepción es un evento de excepción del modo de usuario no detectadas.

`EXCEPTION_STOP_ALL`\
Detener en cualquier excepción. No se utiliza para describir un evento de excepción.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Al describir un evento de excepción, indica que no se puede continuar desde la excepción.

`EXCEPTION_CODE_SUPPORTED`\
Indica que la excepción tiene código que lo admiten. Usan para mostrar una excepción

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Indica que el código de excepción se debe mostrar en formato hexadecimal. Se usan para mostrar una excepción.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Indica que el código de excepción admite JustMyCode. Se usan para mostrar una excepción.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Indica que el depurador de código administrado debe controlar las excepciones. Si no conjunto, el depurador predeterminado controla las excepciones. Esto se pasa a la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método y no se utiliza en el [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NO USE.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NO USE.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
OBSOLETO, NO USE.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
OBSOLETO, NO USE.

## <a name="remarks"></a>Comentarios
Usar como el `dwState` miembro de la [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estructura para indicar el estado de la excepción y lo que puede realizarse sobre él.

Estos valores también se pasan a la [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) método para establecer el estado de todas las excepciones.

Estas marcas se pueden combinar con una operación OR bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
