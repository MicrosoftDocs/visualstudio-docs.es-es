---
title: DEBUG_REASON Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737427"
---
# <a name="debug_reason"></a>DEBUG_REASON
Especifica por qué se inició el proceso para la depuración.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Fields
`DEBUG_REASON_ERROR`\
Se ha producido un error no específico (esto se utiliza como condición predeterminada cuando no cabe ninguna de las otras razones).

`DEBUG_REASON_USER_LAUNCHED`\
El proceso se inició a petición del usuario.

`DEBUG_REASON_USER_ATTACHED`\
El proceso ya en ejecución fue asociado por el usuario.

`DEBUG_REASON_AUTO_ATTACHED`\
El proceso se adjuntó automáticamente al momento en que se inició.

`DEBUG_REASON_CAUSALITY`\
El proceso se inició debido a un evento de depuración *Just-In-Time* (JIT).

## <a name="remarks"></a>Observaciones
Se devuelve desde el [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
