---
title: "IDebugPendingBreakpoint2::EnumErrorBreakpoints | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::EnumErrorBreakpoints"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::EnumErrorBreakpoints (método)"
  - "EnumErrorBreakpoints (método)"
ms.assetid: 2f9a9720-c1ac-4430-8f28-200d85360452
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::EnumErrorBreakpoints
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene una lista de todos los puntos de interrupción de errores resultantes de este punto de interrupción pendiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumErrorBreakpoints(   
   BP_ERROR_TYPE                 bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```c#  
int EnumErrorBreakpoints(   
   enum_BP_ERROR_TYPE              bpErrorType,  
   out IEnumDebugErrorBreakpoints2 ppEnum  
);  
```  
  
#### Parámetros  
 `bpErrorType`  
 \[in\]  Una combinación de valores de enumeración de [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) que selecciona el tipo de errores enumerar.  
  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) que contiene una lista de objetos de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CPendingBreakpoint` que expone la interfaz de [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
```cpp#  
HRESULT CPendingBreakpoint::EnumErrorBreakpoints(  
   BP_ERROR_TYPE bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum)    
{    
   HRESULT hr;    
  
   // Verify that the passed IEnumDebugErrorBreakpoints2 interface pointer   
   // is valid.    
   if (ppEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that this error is not a warning.    
         // All errors supported by this DE are errors, not warnings.    
         if (IsFlagSet(bpErrorType, BPET_TYPE_ERROR) && m_pErrorBP)    
         {    
            // Get the error breakpoint.    
            CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
            hr = m_pErrorBP->QueryInterface(&spErrorBP);    
            assert(hr == S_OK);    
            if (hr == S_OK)    
            {    
               // Create the error breakpoint enumerator.    
               CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
               hr = CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum);    
               assert(hr == S_OK);    
               if (hr == S_OK)    
               {    
                  // Initialize the enumerator of error breakpoints with   
                  // the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hr = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hr == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be queried by the created   
                     // CEnumDebugErrorBreakpoints object.    
                     hr = pErrorEnum->QueryInterface(ppEnum);    
                     assert(hr == S_OK);    
                  }    
  
                  // Otherwise, delete the CEnumDebugErrorBreakpoints   
                  // object.    
                  if (FAILED(hr))    
                  {    
                     delete pErrorEnum;    
                  }    
               }    
            }    
         }    
         else    
         {    
            hr = S_FALSE;    
         }    
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
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)