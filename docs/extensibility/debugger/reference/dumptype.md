---
description: Especifica la cantidad del estado de un programa (como la ejecución de subprocesos, marcos de pila y dirección de instrucción actual) que se va a volcar.
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cef9f90c1f08dac742a6f01a4dd48f6bff76848b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150983"
---
# <a name="dumptype"></a>DUMPTYPE
Especifica la cantidad del estado de un programa (como la ejecución de subprocesos, marcos de pila y dirección de instrucción actual) que se va a volcar.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Campos
`DUMP_MINIDUMP`\
Especifica un volcado pequeño y compacto.

`DUMP_FULLDUMP`\
Especifica un volcado de memoria completo y grande.

## <a name="remarks"></a>Observaciones
Se pasa como argumento al método [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
