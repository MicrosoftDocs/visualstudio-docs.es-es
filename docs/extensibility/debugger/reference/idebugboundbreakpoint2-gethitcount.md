---
title: "IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetHitCount"
helpviewer_keywords: 
  - "GetHitCount (método)"
  - "IDebugBoundBreakpoint2::GetHitCount (método)"
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el número de llamadas actual para esto limitan el punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```c#  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### Parámetros  
 `pdwHitCount`  
 \[out\]  Devuelve el número de llamadas.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_BP_DELETED` si establece el estado del objeto enlazado de punto de interrupción a `BPS_DELETED` \(parte de la enumeración de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) \).  
  
## Comentarios  
 El número de llamadas es el número de veces que este punto de interrupción ha desencadenado durante la ejecución de la actual de la sesión.  
  
## Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)