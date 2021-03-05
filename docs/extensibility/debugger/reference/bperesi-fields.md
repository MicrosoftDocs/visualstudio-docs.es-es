---
description: Especifica la información que se va a recuperar sobre una resolución errónea de un punto de interrupción.
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26b5a7285c2e5c9135429777b4b58f35252e550
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162529"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Especifica la información que se va a recuperar sobre una resolución errónea de un punto de interrupción.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`PERESI_BPRESLOCATION`\
Inicialice/use el `bpResLocation` campo (ubicación de resolución de puntos de interrupción) de la estructura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .

`BPERESI_PROGRAM`\
Inicialice o use el `pProgram` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

`BPERESI_THREAD`\
Inicialice o use el `pThread` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

`BPERESI_MESSAGE`\
Inicialice o use el `bstrMessage` campo de la `BP_ERROR_RESOLUTION_INFO` estructura.

`BPERESI_TYPE`\
Inicialice/use el `dwType` campo (tipo de punto de interrupción) de la `BP_ERROR_RESOLUTION_INFO` estructura.

`BPERESI_ALLFIELDS`\
Inicializar o utilizar todos los campos de la `BP_ERROR_RESOLUTION_INFO` estructura.

## <a name="remarks"></a>Observaciones
Se pasa como un parámetro al método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) para indicar qué campos de la estructura de [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) se van a inicializar.

Estos valores también se usan para indicar qué campos de la `BP_ERROR_RESOLUTION_INFO` estructura se usan y son válidos cuando se devuelve esa estructura.

Estos valores se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
