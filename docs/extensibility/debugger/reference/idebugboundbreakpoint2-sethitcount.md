---
title: "IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetHitCount"
helpviewer_keywords: 
  - "SetHitCount (método)"
  - "IDebugBoundBreakpoint2::SetHitCount (método)"
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::SetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el número de llamadas para el punto de interrupción enlazado.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```c#  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### Parámetros  
 `dwHitCount`  
 \[in\]  El número de llamadas al conjunto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_BP_DELETED` si establece el estado del objeto enlazado de punto de interrupción a `BPS_DELETED` \(parte de la enumeración de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Comentarios  
 El número de llamadas es el número de veces que este punto de interrupción ha desencadenado durante la ejecución de la actual de la sesión.  
  
 Este método llama normalmente por el motor de depuración para actualizar el número de llamadas actual en este punto de interrupción.  
  
## Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)