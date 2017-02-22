---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz indica al administrador de depuración de la sesión \(SDM\) que un punto de interrupción pendiente no se puede enlazar a un programa carga, debido a una advertencia o un error.  
  
## Sintaxis  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz como parte de su compatibilidad para los puntos de interrupción.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz \(el SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` \).  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event cuando un punto de interrupción pendiente no se puede enlazar al programa que se depura.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugBreakpointErrorEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtiene la interfaz de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) que describe la advertencia o error.|  
  
## Comentarios  
 Siempre que se enlaza un punto de interrupción, un evento se envía al SDM.  Si el punto de interrupción no puede estar enlazado, se envía `IDebugBreakpointErrorEvent2` ; si no, se envía [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) .  
  
 Por ejemplo, cuando la condición asociada al punto de interrupción pendiente no puede analizar o para evaluar, se envía una advertencia que el punto de interrupción pendiente no se puede enlazar en este momento.  Esto puede ocurrir si el código para el punto de interrupción no ha cargado todavía.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)