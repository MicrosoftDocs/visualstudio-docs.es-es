---
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7edb3129733aec29bb5eda64d388024bec4d5ece
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318191"
---
# <a name="dumptype"></a>DUMPTYPE
Especifica qué parte del estado de un programa (por ejemplo, los subprocesos en ejecución, marcos de pila y dirección de la instrucción actual) para volcar.

## <a name="syntax"></a>Sintaxis

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
Especifica un volcado de memoria pequeño y compacto.

`DUMP_FULLDUMP`\
Especifica un volcado de memoria grande, completa.

## <a name="remarks"></a>Comentarios
Se pasa como argumento a la [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
