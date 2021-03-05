---
description: Especifica el tipo de nombre de host.
title: GETHOSTNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3354bdbceeac796e2761bb83a5d860ca8a716315
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150788"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
Especifica el tipo de nombre de host.

## <a name="syntax"></a>Syntax

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>Campos
`GHN_FRIENDLY_NAME`\
Especifica un nombre descriptivo del host.

`GHN_FILE_NAME`\
Especifica un nombre de archivo del host.

## <a name="remarks"></a>Observaciones
Estos valores se pasan como argumento al método [GetHostName (](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) para recuperar un nombre de host en formatos diferentes.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
