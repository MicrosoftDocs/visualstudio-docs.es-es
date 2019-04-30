---
title: IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88fde36e2d7b0ef776849d7d3af7e36418dfff7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877400"
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

#### <a name="parameters"></a>Parámetros
 `pdwHitCount`

 [out] Devuelve el número de llamadas.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se establece el estado del objeto de punto de interrupción enlazado en `BPS_DELETED` (parte de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración).

## <a name="remarks"></a>Comentarios
 El número de llamadas es el número de veces que se ha activado este punto de interrupción durante la ejecución de la sesión actual.

## <a name="see-also"></a>Vea también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)