---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18861d7aa19281528e9a100f57399451194598a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327250"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Se usa para determinar si un programa puede detener la ejecución después de alcanzar un punto concreto en la ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Campos
`CANSTOP_ENTRYPOINT`\
Especifica el punto de entrada del programa determinado.

`CANSTOP_STEPIN`\
Especifica la ejecución paso a paso en una función.

## <a name="remarks"></a>Comentarios
Se pasa como argumento a la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método confirmar con la sesión de depuración Manager (SDM) si es aceptable para detenerse después de alcanzar el punto de entrada del programa o después de la ejecución paso a paso en una función o método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
