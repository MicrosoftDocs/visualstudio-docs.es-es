---
description: Obtiene el número de llamadas actual para este punto de interrupción enlazado.
title: 'IDebugBoundBreakpoint2:: GetHitCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca015a814956a0b6073e090d17751e623b557429
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088865"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Obtiene el número de llamadas actual para este punto de interrupción enlazado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>Parámetros
`pdwHitCount`\
enuncia Devuelve el número de llamadas.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si el estado del objeto de punto de interrupción enlazado se establece en `BPS_DELETED` (parte de la enumeración [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Observaciones
 El número de llamadas es el número de veces que se ha desencadenado este punto de interrupción durante la ejecución actual de la sesión.

## <a name="see-also"></a>Consulte también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
