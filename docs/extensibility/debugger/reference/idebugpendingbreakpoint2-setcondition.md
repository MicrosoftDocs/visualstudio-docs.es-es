---
description: Establece o cambia la condición asociada con el punto de interrupción pendiente.
title: 'IDebugPendingBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea2ce1a5a9ffdfb48e0190dc3399ceabf5cb052
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142900"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Establece o cambia la condición asociada con el punto de interrupción pendiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parámetros
`bpCondition`\
de Estructura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que especifica la condición que se va a establecer.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se pierde cualquier condición que se asoció previamente al punto de interrupción pendiente. Se llama a todos los puntos de interrupción enlazados desde este punto de interrupción pendiente para establecer su condición en el valor especificado en el `bpCondition` parámetro.

## <a name="see-also"></a>Consulte también
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
