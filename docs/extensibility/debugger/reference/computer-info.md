---
title: COMPUTER_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737658"
---
# <a name="computer_info"></a>COMPUTER_INFO
Describe el equipo en el que se ejecuta el depurador.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Miembros
`wProcessorArchitecture`\
Identifica la arquitectura del microprocesador.

`wSuiteMask`\
Identifica la máscara de suite.

`dwOperatingSystemVersion`\
Número de versión del sistema operativo.

## <a name="remarks"></a>Observaciones
Esta estructura es devuelta por el [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
