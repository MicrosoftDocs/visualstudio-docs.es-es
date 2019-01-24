---
title: IDebugBoundBreakpoint2::SetPassCount | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ee22a1fe94836ac61dad2c98b69b02d63dbc69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952198"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Establece o cambia el número de paso asociado a este punto de interrupción enlazado.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `bpPassCount`  
 [in] El [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que especifica el recuento de pass.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se establece el estado del objeto de punto de interrupción enlazado en `BPS_DELETED` (parte de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración).  
  
## <a name="remarks"></a>Comentarios  
 El recuento de pass determina cuándo se desencadena el punto de interrupción. El paso actual o el número de llamadas se puede obtener mediante una llamada a la [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) método.  
  
 Se pierde cualquier contador de pasos que estaba asociado previamente a este punto de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)