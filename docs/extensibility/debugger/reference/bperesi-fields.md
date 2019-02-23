---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 488c2b1a96d01e0e7dfa9868d2f7e5111adc4e2d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699436"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Especifica la información que se va a recuperar acerca de una solución con errores de un punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="members"></a>Miembros
PERESI_BPRESLOCATION Initialize o usar el `bpResLocation` campo (ubicación de la resolución de punto de interrupción) de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura.

BPERESI_PROGRAM Initialize o usar el `pProgram` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

BPERESI_THREAD Initialize o usar el `pThread` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

BPERESI_MESSAGE Initialize o usar el `bstrMessage` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

BPERESI_TYPE Initialize o usar el `dwType` campo (tipo de punto de interrupción) de la `BP_ERROR_RESOLUTION_INFO` estructura.

BPERESI_ALLFIELDS Initialize o usar todos los campos de la `BP_ERROR_RESOLUTION_INFO` estructura.

## <a name="remarks"></a>Comentarios
Pasado como parámetro a la [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método para indicar qué campos de la [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura deben inicializarse.

Estos valores también se usan para indicar qué campos de la `BP_ERROR_RESOLUTION_INFO` estructura se usan y válido cuando se devuelve esa estructura.

Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
