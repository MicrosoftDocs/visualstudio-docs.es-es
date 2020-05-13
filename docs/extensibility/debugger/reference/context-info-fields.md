---
title: CONTEXT_INFO_FIELDS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737591"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Especifica qué información se va a recuperar sobre un contexto de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Fields
`CIF_MODULEURL`\
Inicializar/utilizar `bstrModuleUrl` el campo de la estructura [CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md)

`CIF_FUNCTION`\
Inicializar/utilizar `bstrFunction` el campo `CONTEXT_INFO` de la estructura.

`CIF_FUNCTIONOFFSET`\
Inicializar/utilizar `posFunctionOffset` el campo `CONTEXT_INFO` de la estructura.

`CIF_ADDRESS`\
Inicializar/utilizar `bstrAddress` el campo `CONTEXT_INFO` de la estructura.

`CIF_ADDRESSOFFSET`\
Inicializar/utilizar `bstrAddressOffset` el campo `CONTEXT_INFO` de la estructura.

`CIF_ALLFIELDS`\
Inicializar/utilizar todos los `CONTEXT_INFO` campos de la estructura.

## <a name="remarks"></a>Observaciones
Estos valores se pasan un parámetro a la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método para indicar qué campos de la [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estructura se van a inicializar.

Estos indicadores también se utilizan `CONTEXT_INFO` para indicar qué campos de la estructura se utilizan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar con un OR bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
