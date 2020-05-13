---
title: IDebugThread2::GetLogicalThread ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718840"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Los motores de depuración no implementan este método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parámetros
`pStackFrame`\
[en] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa el marco de pila.

`ppLogicalThread`\
[fuera] Devuelve `IDebugLogicalThread2` una interfaz que representa el subproceso lógico asociado. Una implementación del motor de depuración debe establecer esto en un valor nulo.

## <a name="return-value"></a>Valor devuelto
 Las implementaciones del `E_NOTIMPL`motor de depuración siempre devuelven .

## <a name="see-also"></a>Vea también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
