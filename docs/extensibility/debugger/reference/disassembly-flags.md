---
title: DISASSEMBLY_FLAGS de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737376"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Especifica las marcas para el desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Fields
`DF_DOCUMENTCHANGE`\
Indica que esta instrucción está en un documento diferente al anterior.

`DF_DISABLED`\
Indica que esta instrucción no se ejecutará.

`DF_INSTRUCTION_ACTIVE`\
Indica que esta instrucción es una de las siguientes instrucciones que se van a ejecutar (puede haber más de una).

`DF_DATA`\
Indica que esta instrucción es realmente datos (no código).

`DF_HASSOURCE`\
Indica que esta instrucción tiene origen. Algunas instrucciones, como la generación de perfiles o el código de recolección de elementos no utilizados, no tienen ningún origen correspondiente.

`DF_DOCUMENT_CHECKSUM`\
Indica que `bstrDocumentUrl` el campo contiene datos de suma de comprobación después de la dirección URL del documento. Consulte la sección Comentarios para la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) para ver cómo se almacenan los datos de suma de comprobación.

## <a name="remarks"></a>Observaciones
Se utiliza `dwFlags` como miembro de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura.

Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
