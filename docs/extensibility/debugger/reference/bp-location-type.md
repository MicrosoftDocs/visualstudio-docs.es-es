---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 735acca4d4b2e2881c49a236dadae44aaa3cc1fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902137"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Especifica el tipo de ubicación del punto de interrupción para una solicitud de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Campos
`BPLT_NONE`\
No especifica ninguna ubicación de punto de interrupción.

`BPLT_FILE_LINE`\
Especifica el tipo de ubicación del punto de interrupción como una línea de archivo.

`BPLT_FUNC_OFFSET`\
Especifica el tipo de ubicación del punto de interrupción como un desplazamiento de función.

`BPLT_CONTEXT`\
Especifica el tipo de ubicación del punto de interrupción como un contexto.

`BPLT_STRING`\
Especifica el tipo de ubicación del punto de interrupción como una cadena.

`BPLT_ADDRESS`\
Especifica el tipo de ubicación del punto de interrupción como una dirección.

`BPLT_RESOLUTION`\
Especifica el tipo de ubicación del punto de interrupción como una resolución.

`BPLT_CODE_FILE_LINE`\
Especifica el tipo de ubicación del punto de interrupción como una línea de código fuente.

`BPLT_CODE_FUNC_OFFSET`\
Especifica el tipo de ubicación del punto de interrupción como desplazamiento de función de código.

`BPLT_CODE_CONTEXT`\
Especifica el tipo de ubicación del punto de interrupción como contexto de código.

`BPLT_CODE_STRING`\
Especifica el tipo de ubicación del punto de interrupción como una cadena de código.

`BPLT_CODE_ADDRESS`\
Especifica el tipo de ubicación del punto de interrupción como una dirección de código.

`BPLT_DATA_STRING`\
Especifica el tipo de ubicación del punto de interrupción como una cadena de datos.

`BPLT_TYPE_MASK`\
Especifica una máscara de bits, de modo que el tipo de punto de interrupción se puede extraer del valor.

`BPLT_LOCATION_TYPE_MASK`\
Especifica una máscara de bits, de modo que el tipo de ubicación del punto de interrupción se puede extraer del valor.

## <a name="remarks"></a>Notas
Se pasa como un parámetro al método [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .

Un tipo de ubicación de punto de interrupción se compone de un tipo de punto de interrupción y un tipo de ubicación. Esto significa que un tipo de ubicación de punto de interrupción nunca es simplemente un tipo de punto de interrupción (por ejemplo, `BPT_CODE` ) o un tipo de ubicación (por ejemplo, `BPLT_FILE_LINE` ). Las constantes predefinidas para todos los tipos de ubicación de puntos de interrupción admitidos actualmente se incluyen en esta enumeración ( `BPLT_CODE_FILE_LINE` a `BPLT_DATA_STRING` ).

`BPT_CODE` y `BPT_DATA` son miembros de la enumeración [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
