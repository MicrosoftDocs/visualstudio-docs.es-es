---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737591"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Especifica la información que se va a recuperar sobre un contexto de memoria.

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

## <a name="fields"></a>Campos
`CIF_MODULEURL`\
Inicialice o utilice el `bstrModuleUrl` campo de la estructura de [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) .

`CIF_FUNCTION`\
Inicialice o use el `bstrFunction` campo de la `CONTEXT_INFO` estructura.

`CIF_FUNCTIONOFFSET`\
Inicialice o use el `posFunctionOffset` campo de la `CONTEXT_INFO` estructura.

`CIF_ADDRESS`\
Inicialice o use el `bstrAddress` campo de la `CONTEXT_INFO` estructura.

`CIF_ADDRESSOFFSET`\
Inicialice o use el `bstrAddressOffset` campo de la `CONTEXT_INFO` estructura.

`CIF_ALLFIELDS`\
Inicializar o utilizar todos los campos de la `CONTEXT_INFO` estructura.

## <a name="remarks"></a>Observaciones
Estos valores pasan un parámetro al método [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) para indicar qué campos de la estructura de [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) se van a inicializar.

Estas marcas también se usan para indicar los campos de la `CONTEXT_INFO` estructura que se usan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar con una operación OR bit a bit.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
