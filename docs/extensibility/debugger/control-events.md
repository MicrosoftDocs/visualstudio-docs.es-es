---
title: Control de eventos | Microsoft Docs
description: Obtenga información sobre el envío de eventos durante la ejecución controlada del programa mediante la interfaz IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb7249ece3ab38ff6f378f3c48ce36a995677604
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905701"
---
# <a name="control-events"></a>Eventos de control
Debe enviar eventos durante la ejecución controlada del programa. Todos los eventos se envían mediante la interfaz [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) y tienen atributos que requieren que implemente el [método IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Otros métodos
 Algunos eventos requieren la implementación de métodos adicionales, como se muestra a continuación:

- El envío de la interfaz [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) cuando se inicializa el motor de depuración (DE) requiere que implemente el método [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- El control de ejecución requiere la implementación de eventos de control como las interfaces [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) [e IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** solo es necesario para interrupciones asincrónicas.

- La ejecución paso a paso por procedimientos de las funciones requiere la implementación de [la interfaz IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) y sus métodos.

  Los eventos derivados de puntos de interrupción requieren la implementación de las interfaces [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) así como los métodos [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  La evaluación de expresiones asincrónicas requiere que implemente la interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) y sus métodos [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[y GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Los eventos sincrónicos requieren implementar [el método IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Para que el motor escriba una salida de estilo de cadena, debe implementar el [método IDebugOutputStringEvent2::GetString.](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)

## <a name="see-also"></a>Consulta también
- [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
