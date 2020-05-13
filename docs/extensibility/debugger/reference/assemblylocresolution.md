---
title: ASSEMBLYLOCRESOLUTION ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbd015408cbefd1861f6e795447a5302efabb0dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738139"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Especifica dónde se encuentra un ensamblaje.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Fields
`ALR_NAME`\
Ensamblado se encuentra en el espacio de nombres actual.

`ALR_USERDIR`\
El ensamblado se encuentra en un directorio de usuario.

`ALR_SHAREDDIR`\
El ensamblado se encuentra en el directorio compartido.

`ALR_REMOTEDIR`\
El ensamblado se encuentra en un directorio remoto.

## <a name="remarks"></a>Observaciones
Estos valores se devuelven mediante el [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) y [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) métodos.

Estos valores se pueden `OR` combinar con la operación.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
