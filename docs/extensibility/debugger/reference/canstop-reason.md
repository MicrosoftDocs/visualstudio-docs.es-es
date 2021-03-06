---
description: Se utiliza para determinar si un programa puede detener la ejecución después de alcanzar un punto determinado en la ejecución.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a22a0534a464e9899e666550b31ab24503c05d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096530"
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

## <a name="fields"></a>Campos
`CANSTOP_ENTRYPOINT`\
Especifica el punto de entrada del programa determinado.

`CANSTOP_STEPIN`\
Especifica la ejecución paso a paso de una función.

## <a name="remarks"></a>Observaciones
Se pasa como argumento al método [GetReason (](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para confirmar con el administrador de depuración de sesión (SDM) si es correcto detenerse después de alcanzar el punto de entrada del programa o después de entrar en una función o un método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
