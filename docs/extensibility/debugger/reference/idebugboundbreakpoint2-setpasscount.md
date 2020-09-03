---
title: 'IDebugBoundBreakpoint2:: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735431"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Establece o cambia el número de pasos asociado a este punto de interrupción enlazado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parámetros
`bpPassCount`\
de Estructura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que especifica el número de pasos.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si el estado del objeto de punto de interrupción enlazado se establece en `BPS_DELETED` (parte de la enumeración [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Observaciones
 El número de pasos determina cuándo se activa el punto de interrupción. El número de llamadas o el paso actual se puede obtener llamando al método [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) .

 Se pierde cualquier recuento de pasos que se asoció previamente con este punto de interrupción.

## <a name="see-also"></a>Vea también
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
