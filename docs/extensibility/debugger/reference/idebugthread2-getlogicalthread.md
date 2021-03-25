---
description: Los motores de depuración no implementan este método.
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe053a15ca6c89167b4b4cbf9bdffc8d7c334e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070978"
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
de Un objeto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa el marco de pila.

`ppLogicalThread`\
enuncia Devuelve una `IDebugLogicalThread2` interfaz que representa el subproceso lógico asociado. Una implementación del motor de depuración debe establecerlo en un valor null.

## <a name="return-value"></a>Valor devuelto
 Las implementaciones del motor de depuración siempre devuelven `E_NOTIMPL` .

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
