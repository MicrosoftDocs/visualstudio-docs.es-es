---
title: DISASSEMBLY_STREAM_FIELDS de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737354"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Especifica qué información se va a recuperar sobre un campo de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Fields
`DSF_ADDRESS`\
Inicializar/utilizar `bstrAddress` el campo.

`DSF_ADDRESSOFFSET`\
Inicializar/utilizar `bstrAddressOffset` el campo.

`DSF_CODEBYTES`\
Inicializar/utilizar `bstrCodeBytes` el campo.

`DSF_OPCODE`\
Inicializar/utilizar `bstrOpCode` el campo.

`DSF_OPERANDS`\
Inicializar/utilizar `bstrOperands` el campo.

`DSF_SYMBOL`\
Inicializar/utilizar `bstrSymbol` el campo.

`DSF_CODELOCATIONID`\
Inicializar/utilizar `uCodeLocationId` el campo.

`DSF_POSITION`\
Inicializar/utilizar `posBeg` los `posEnd` campos y.

`DSF_DOCUMENTURL`\
Inicializar/utilizar `bstrDocumentUrl` el campo.

`DSF_BYTEOFFSET`\
Inicializar/utilizar `dwByteOffset` el campo.

`DSF_FLAGS`\
Inicializar/utilizar `dwFlags` el campo ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Incluya nombres de `bstrOperands` símbolos en el campo.

`DSF_ALL`\
Especifica todos los campos de la secuencia de desensamblado.

## <a name="remarks"></a>Observaciones
Se pasa como parámetro al método [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) para indicar qué campos de la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) se van a inicializar.

Se utiliza `dwFields` para `DisassemblyData` el miembro de la estructura para indicar qué campos se utilizan y son válidos cuando se devuelve la estructura.

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
