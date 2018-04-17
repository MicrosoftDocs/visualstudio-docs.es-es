---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a9b08909bc3d10c80caa5dcf6350368066ca6c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Obtiene el punto de interrupción pendiente que se va a enlazar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```cpp  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppPendingBP`  
 [out] Devuelve el [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el punto de interrupción pendiente que se va a enlazar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo implementar este método para un **CBreakpointSetDebugEventBase** objeto que expone la [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaz.  
  
```cpp  
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2 **ppPendingBP)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppPendingBP )  
    {  
        if ( m_pPendingBP )  
        {  
            *ppPendingBP = m_pPendingBP;  
  
            m_pPendingBP->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)