---
description: Especifica la razón por la que se inició el proceso para la depuración.
title: DEBUG_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9404e4b5cfdd1f1690b0fe76d0cd5e98cc90d2a4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170554"
---
# <a name="debug_reason"></a>DEBUG_REASON
Especifica la razón por la que se inició el proceso para la depuración.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Campos
`DEBUG_REASON_ERROR`\
Se produjo un error no específico (se usa como condición predeterminada cuando no cabe ninguna de las otras razones).

`DEBUG_REASON_USER_LAUNCHED`\
El proceso se inició en la solicitud del usuario.

`DEBUG_REASON_USER_ATTACHED`\
El usuario ha adjuntado el proceso que ya se está ejecutando.

`DEBUG_REASON_AUTO_ATTACHED`\
El proceso se adjuntó automáticamente al iniciarse.

`DEBUG_REASON_CAUSALITY`\
El proceso se ha iniciado debido a un evento de depuración *Just-in-Time* (JIT).

## <a name="remarks"></a>Observaciones
Se devuelve desde el método [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
