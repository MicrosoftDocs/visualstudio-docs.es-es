---
description: Especifica las marcas del desensamblado.
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aeaf00e7073cd1146dcc5856684ed7209e7d800
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170489"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Especifica las marcas del desensamblado.

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>Campos
`DF_DOCUMENTCHANGE`\
Indica que esta instrucción está en un documento diferente al anterior.

`DF_DISABLED`\
Indica que esta instrucción no se ejecutará.

`DF_INSTRUCTION_ACTIVE`\
Indica que esta instrucción es una de las instrucciones siguientes que se van a ejecutar (puede haber más de una).

`DF_DATA`\
Indica que esta instrucción es realmente datos (no código).

`DF_HASSOURCE`\
Indica que esta instrucción tiene el origen. Algunas instrucciones, como la generación de perfiles o el código de recolección de elementos no utilizados, no tienen ningún origen correspondiente.

`DF_DOCUMENT_CHECKSUM`\
Indica que `bstrDocumentUrl` el campo contiene datos de suma de comprobación después de la dirección URL del documento. Vea la sección Comentarios de la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) para saber cómo se almacenan los datos de la suma de comprobación.

## <a name="remarks"></a>Observaciones
Se usa como `dwFlags` miembro de la estructura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .

Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
