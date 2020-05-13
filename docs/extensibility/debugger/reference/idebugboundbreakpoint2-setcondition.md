---
title: IDebugBoundBreakpoint2::SetCondition ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23fbe1b353378ca521fa802bdeae25fd12476df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735463"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Establece o cambia la condición asociada a este punto de interrupción enlazado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parámetros
`bpCondition`\
[en] Valor de la [enumeración BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que describe la condición.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si el estado del objeto de `BPS_DELETED` punto de interrupción enlazado se establece en (parte de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración).

## <a name="remarks"></a>Observaciones
 Se pierde cualquier condición que se haya asociado anteriormente a este punto de interrupción.

## <a name="see-also"></a>Vea también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
