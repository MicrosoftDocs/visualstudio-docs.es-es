---
title: "IDebugBoundBreakpoint2::GetPendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetPendingBreakpoint"
helpviewer_keywords: 
  - "IDebugBoundBreakpoint2::GetPendingBreakpoint (método)"
  - "GetPendingBreakpoint (método)"
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::GetPendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el punto de interrupción pendiente de que el punto de interrupción enlazado especificado se creó.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```c#  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### Parámetros  
 `ppPendingBreakpoint`  
 \[out\]  Devuelve el objeto de [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el punto de interrupción pendiente que se utilizó para crear esta limita el punto de interrupción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un punto de interrupción pendiente se puede considerar como una colección de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o a muchos programas.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CBoundBreakpoint` que expone la interfaz de [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
```  
HRESULT CBoundBreakpoint::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2** ppPendingBreakpoint)  
{    
   HRESULT hr;    
  
   // Check for valid IDebugPendingBreakpoint2 interface pointer.    
   if (ppPendingBreakpoint)    
   {    
      // Be sure that the bound breakpoint has not been deleted. If  
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugPendingBreakpoint2 interface.    
         hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,  
                                           (void**)ppPendingBreakpoint);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
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
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)