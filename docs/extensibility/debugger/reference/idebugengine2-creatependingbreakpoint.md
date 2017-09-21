---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un punto de interrupción pendiente en el motor de depuración \(DE\).  
  
## Sintaxis  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### Parámetros  
 `pBPRequest`  
 \[in\]  un objeto de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que describe el punto de interrupción pendiente para crear.  
  
 `ppPendingBP`  
 \[out\]  Devuelve un objeto de [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el punto de interrupción pendiente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve normalmente `E_FAIL` si no coincide con el parámetro de `pBPRequest` ningún lenguaje admitido por el De si el parámetro de `pBPRequest` no es válido o incompleto.  
  
## Comentarios  
 Un punto de interrupción pendiente es básicamente una colección de toda la información necesaria para enlazar un punto de interrupción en el código.  El punto de interrupción pendiente devuelto por este método no se enlaza al código hasta que se llame al método de [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .  
  
 Para cada punto de interrupción pendiente conjuntos de usuarios, el administrador de depuración de sesión \(SDM\) llaman a este método en cada OF asociado.  Es el OF para comprobar que el punto de interrupción es válido para los programas que se ejecutan en ese OF.  
  
 Cuando el usuario establece un punto de interrupción en una línea de código, el OF quedan libres para enlazar el punto de interrupción a la línea más cercana del documento que corresponde a este código.  Esto permite que el usuario establezca un punto de interrupción en la primera línea de una instrucción de varias líneas, pero lo enlaza en la última línea \(donde todo el código se admite en la información de depuración\).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CProgram` .  La implementación De de `IDebugEngine2::CreatePendingBreakpoint` podría a reenviar todas las llamadas a esta implementación del método en cada programa.  
  
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
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)