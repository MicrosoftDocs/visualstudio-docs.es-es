---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount (método)"
  - "IDebugPendingBreakpoint2::SetPassCount (método)"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece o cambia el recuento de paso asociado al punto de interrupción pendiente.  
  
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
 \[in\]  Una estructura de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contiene el recuento del paso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.  
  
## Comentarios  
 Se pierde cualquier número de paso que estuviera previamente asociado al punto de interrupción pendiente.  Todos los puntos de interrupción enlazados de este punto de interrupción pendiente se denominan para establecer el número de paso al parámetro de `bpPassCount` .  
  
## Vea también  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)