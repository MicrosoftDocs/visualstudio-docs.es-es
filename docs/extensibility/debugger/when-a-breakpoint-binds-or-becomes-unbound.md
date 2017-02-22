---
title: "Cuando enlaza un punto de interrupci&#243;n, o se convierte en independiente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], punto de interrupción sin enlazar eventos"
  - "punto de interrupción enlazado a eventos"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Cuando enlaza un punto de interrupci&#243;n, o se convierte en independiente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando un punto de interrupción no puede enlazarse en ese momento se realiza una llamada al método de [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , el tiempo de enlace y la hora de creación de punto de interrupción es diferente.  
  
## métodos denominados  
 El administrador de depuración de sesión \(SDM\) llama a los métodos siguientes:  
  
1.  [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  El OF devuelve [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2.  [IDebugPendingBreakpoint2:: Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3.  [IDebugPendingBreakpoint2:: Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4.  el método de [IDebugPendingBreakpoint2:: enlace](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) y devuelve S\_OK.  El OF envía [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5.  Métodos de[IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y de [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para comprobar y obtener los puntos de interrupción enlazados.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)