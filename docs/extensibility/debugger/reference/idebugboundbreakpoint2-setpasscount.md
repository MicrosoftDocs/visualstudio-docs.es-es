---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount (método)"
  - "IDebugBoundBreakpoint2::SetPassCount (método)"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece o cambia el recuento de paso asociado a este punto de interrupción enlazado.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Parámetros  
 `bpPassCount`  
 \[in\]  La estructura de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que especifica el recuento del paso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_BP_DELETED` si establece el estado del objeto enlazado de punto de interrupción a `BPS_DELETED` \(parte de la enumeración de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Comentarios  
 El recuento del paso determina cuándo se desencadena el punto de interrupción.  El paso o el número de llamadas actual se puede obtener llamando al método de [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) .  
  
 Se pierde cualquier número de paso que estuviera previamente asociado a este punto de interrupción.  
  
## Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)