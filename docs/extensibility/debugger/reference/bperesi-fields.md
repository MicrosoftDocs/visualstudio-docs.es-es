---
title: BPERESI_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737767"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Especifica la información que se va a recuperar sobre una resolución con errores de un punto de interrupción.

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

## <a name="fields"></a>Fields
`PERESI_BPRESLOCATION`\
Inicializar/utilizar `bpResLocation` el campo (ubicación de resolución de punto de interrupción) de la [estructura BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Inicializar/utilizar `pProgram` el campo `BP_ERROR_RESOLUTION_INFO` de la estructura.

`BPERESI_THREAD`\
Inicializar/utilizar `pThread` el campo `BP_ERROR_RESOLUTION_INFO` de la estructura.

`BPERESI_MESSAGE`\
Inicializar/utilizar `bstrMessage` el campo `BP_ERROR_RESOLUTION_INFO` de la estructura.

`BPERESI_TYPE`\
Inicializar/utilizar `dwType` el campo (tipo de `BP_ERROR_RESOLUTION_INFO` punto de interrupción) de la estructura.

`BPERESI_ALLFIELDS`\
Inicializar/utilizar todos los `BP_ERROR_RESOLUTION_INFO` campos de la estructura.

## <a name="remarks"></a>Observaciones
Se pasa como parámetro al método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) para indicar qué campos de la estructura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) se van a inicializar.

Estos valores también se utilizan para `BP_ERROR_RESOLUTION_INFO` indicar qué campos de la estructura se utilizan y son válidos cuando se devuelve esa estructura.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
