---
title: Controlar eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3220e3c6ef1a20b8a434fbfab13b419beb331032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="control-events"></a>Eventos de control
Debe enviar eventos durante la ejecución del programa controlada. Todos los eventos se envían con el [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) de interfaz y tener atributos que requieren que implemente la [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) método.  
  
## <a name="additional-methods"></a>Métodos adicionales  
 Algunos eventos requieren implementación de métodos adicionales, como se indica a continuación:  
  
-   Enviar el [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaz cuando se inicializa el motor de depuración (Alemania) exige que implemente la [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) método.  
  
-   Control de ejecución requiere la implementación de los eventos de control, como el [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) y[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaces. **IDebugBreakEvent2** solo es necesario para los saltos de asincrónicos.  
  
-   Ejecución paso a paso en funciones requiere la implementación de la [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaz y sus métodos.  
  
 Eventos de derivar de los puntos de interrupción requieren la implementación de la [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), y [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaces, así como el [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) métodos.  
  
 Evaluación de expresiones asincrónica exige que implemente la [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaz y su [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [y GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) métodos.  
  
 Eventos sincrónicos requieren implementar el [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.  
  
 Para que el motor escribir la salida de estilo de cadena, debe implementar la [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)