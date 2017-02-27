---
title: "IDebugBoundBreakpoint2::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetState"
helpviewer_keywords: 
  - "Método GetState"
  - "IDebugBoundBreakpoint2::GetState (método)"
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el estado de esto limitan el punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```c#  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### Parámetros  
 `pState`  
 \[out\]  Devuelve un valor de enumeración de [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) que describe el estado del punto de interrupción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CBoundBreakpoint` que expone la interfaz de [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Vea también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)