---
title: IDebugPendingBreakpoint2::EnumErrorBreakpoints | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints
helpviewer_keywords:
- IDebugPendingBreakpoint2::EnumErrorBreakpoints method
- EnumErrorBreakpoints method
ms.assetid: 2f9a9720-c1ac-4430-8f28-200d85360452
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36ebe62cf005a537b3f7e9cbe35ffe7e8904b758
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781987"
---
# <a name="idebugpendingbreakpoint2enumerrorbreakpoints"></a>IDebugPendingBreakpoint2::EnumErrorBreakpoints
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene una lista de todos los puntos de interrupción de error que dan como resultado de este punto de interrupción pendiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumErrorBreakpoints(   
   BP_ERROR_TYPE                 bpErrorType,  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumErrorBreakpoints(   
   enum_BP_ERROR_TYPE              bpErrorType,  
   out IEnumDebugErrorBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bpErrorType`  
 [in] Una combinación de valores de la [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) enumeración que selecciona el tipo de errores a enumerar.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) objeto que contiene una lista de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) objetos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CPendingBreakpoint` objeto que expone el [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz.  
  
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
  
## <a name="see-also"></a>Vea también  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

