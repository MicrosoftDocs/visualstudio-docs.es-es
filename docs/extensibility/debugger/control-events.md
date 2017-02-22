---
title: "Eventos de control | Microsoft Docs"
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
  - "depurar [SDK de depuración], eventos"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Eventos de control
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debe enviar eventos durante la ejecución controlada del programa.  Todos los eventos se envían mediante la interfaz de [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) y tienen atributos que necesitan implementar el método de [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .  
  
## métodos adicionales  
 algunos eventos requieren la implementación de métodos adicionales, como sigue:  
  
-   El envío de la interfaz de [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) cuando se inicializa el \(DE\) motor de depuración requiere implementar el método de [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .  
  
-   El control de ejecución requiere la implementación de los eventos de control como las interfaces de [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) y de[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) .  **IDebugBreakEvent2** solo se requiere para las interrupciones asincrónicas.  
  
-   La entrada en funciones requiere la implementación de la interfaz de [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) y sus métodos.  
  
 Los eventos que se derivan de los puntos de interrupción requieren la implementación de las interfaces de [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), de [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), y de [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , así como de los métodos de [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y de [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .  
  
 La evaluación asincrónica de la expresión requiere implementar la interfaz de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) y sus métodos de [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[y GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .  
  
 Los eventos sincrónicos necesario implementar el método de [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .  
  
 Para que el motor escriba la salida de cadena\-estilo, debe implementar el método de [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .  
  
## Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)