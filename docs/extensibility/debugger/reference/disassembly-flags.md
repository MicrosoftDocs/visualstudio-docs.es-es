---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ac3a43f64e4284cd14741acde390c930ffbb69
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413285"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Especifica las marcas de desensamblado.

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

## <a name="members"></a>Miembros
DF_DOCUMENTCHANGE  
Indica que esta instrucción está en un documento diferente que el anterior.

DF_DISABLED  
Indica que no se ejecutará esta instrucción.

DF_INSTRUCTION_ACTIVE  
Indica que esta instrucción es una de las instrucciones que se ejecutará siguientes (puede haber más de uno).

DF_DATA  
Indica que esta instrucción es realmente datos (sin codificar).

DF_HASSOURCE  
Indica que esta instrucción tiene código fuente. Algunas instrucciones, por ejemplo, el código de la colección de elementos no utilizados o generación de perfiles, no tengan ningún origen correspondiente.

DF_DOCUMENT_CHECKSUM  
Indica que `bstrDocumentUrl` campo contiene datos de la suma de comprobación después de la dirección URL del documento. Consulte la sección Comentarios para el [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura de cómo se almacenan los datos de la suma de comprobación.

## <a name="remarks"></a>Comentarios
Usar como el `dwFlags` miembro de la [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura.

Estas marcas se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
