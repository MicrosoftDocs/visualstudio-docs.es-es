---
title: IDebugBoundBreakpoint2::GetBreakpointResolution | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d58c58dbbaad6d57518c8f13620029034ae4b76
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920396"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Obtiene la resolución de punto de interrupción que se describe en este punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppBPResolution`  
 [out] Devuelve el [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz que representa uno de los siguientes:  
  
-   El objeto de resolución de punto de interrupción que describe la ubicación en el código donde se ha enlazado un punto de interrupción del código.  
  
-   La ubicación de datos donde se ha enlazado un punto de interrupción de datos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se establece el estado del objeto de punto de interrupción enlazado en `BPS_DELETED` (parte de la [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeración).  
  
## <a name="remarks"></a>Comentarios  
 Llame a la [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) método para determinar si la resolución de punto de interrupción es para código o datos.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CBoundBreakpoint` objeto que expone el [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaz.  
  
```  
HRESULT CBoundBreakpoint::GetBreakpointResolution(  
    IDebugBreakpointResolution2** ppBPResolution)  
{    
   HRESULT hr;    
  
   if (ppBPResolution)    
   {    
      // Verify that the bound breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugBreakpointResolution2 interface.    
         hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,  
                                       (void **)ppBPResolution);  
         assert(hr == S_OK);    
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
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)