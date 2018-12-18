---
title: IDebugEngine2::CreatePendingBreakpoint | Documentos de Microsoft
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
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28123ed555cc54d8ca307cca020fe7b101f73087
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777232"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un punto de interrupción pendiente en el motor de depuración (DE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBPRequest`  
 [in] Un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) objeto que describe el punto de interrupción pendiente a crear.  
  
 `ppPendingBP`  
 [out] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el punto de interrupción pendiente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve normalmente `E_FAIL` si el `pBPRequest` parámetro no coincide con cualquier lenguaje compatible con la DE If el `pBPRequest` parámetro no es válido o incompleto.  
  
## <a name="remarks"></a>Comentarios  
 Un punto de interrupción pendiente es esencialmente una colección de toda la información necesaria para enlazar un punto de interrupción al código. El punto de interrupción pendiente devuelto por este método no está enlazado a código hasta la [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) se llama al método.  
  
 Para cada punto de interrupción pendiente de los conjuntos de usuarios, el Administrador de depuración de la sesión (SDM) llama a este método en cada DE adjunto. Es la DE comprobar que el punto de interrupción es válida para los programas que se ejecutan en ese DE.  
  
 Cuando el usuario establece un punto de interrupción en una línea de código, la DE es gratuita enlazar el punto de interrupción a la línea más próxima en el documento que corresponde a este código. Esto permite al usuario establecer un punto de interrupción en la primera línea de una instrucción multilínea, pero enlazarlo en la última línea (donde todo el código se atribuye la información de depuración).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto. Implementación de la DE la `IDebugEngine2::CreatePendingBreakpoint` , a continuación, se puede reenviar todas las llamadas a esta implementación del método en cada programa.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

