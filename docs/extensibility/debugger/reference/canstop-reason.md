---
title: CANSTOP_REASON Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737689"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Se utiliza para determinar si un programa puede detener la ejecución después de alcanzar un punto determinado en la ejecución.

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

## <a name="fields"></a>Fields
`CANSTOP_ENTRYPOINT`\
Especifica el punto de entrada del programa especificado.

`CANSTOP_STEPIN`\
Especifica el paso a una función.

## <a name="remarks"></a>Observaciones
Se pasa como argumento al método [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para confirmar con el Administrador de depuración de sesiones (SDM) si está bien detenerse después de llegar al punto de entrada del programa o después de entrar en una función o método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
