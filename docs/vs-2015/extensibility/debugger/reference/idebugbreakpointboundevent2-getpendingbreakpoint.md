---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bfd35a8a5942b3ce271c4ef2128b28e64a7db4c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577520"
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint).  
  
Obtiene el punto de interrupción pendiente que se está enlazando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```cpp#  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppPendingBP`  
 [out] Devuelve el [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el punto de interrupción pendiente que se está enlazando.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para un **CBreakpointSetDebugEventBase** objeto que expone el [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaz.  
  
```cpp#  
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

