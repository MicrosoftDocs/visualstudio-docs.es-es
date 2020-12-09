---
title: Eventos de control | Microsoft Docs
description: Obtenga información sobre el envío de eventos durante la ejecución controlada de su programa mediante la interfaz IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf7f59384d9317e4be173c93b6165d754a35ad8f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914249"
---
# <a name="control-events"></a>Eventos de control
Debe enviar eventos durante la ejecución controlada del programa. Todos los eventos se envían mediante la interfaz [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) y tienen atributos que requieren que se implemente el método [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Métodos adicionales
 Algunos eventos requieren la implementación de métodos adicionales, como se indica a continuación:

- El envío de la interfaz [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) cuando se inicializa el motor de depuración (de) requiere que se implemente el método [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- El control de ejecución requiere la implementación de estos eventos de control como las interfaces [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) y[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** solo es necesario para los saltos asincrónicos.

- La ejecución paso a paso de las funciones requiere la implementación de la interfaz [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) y sus métodos.

  Los eventos que se derivan de los puntos de interrupción requieren la implementación de las interfaces [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)y [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , así como los métodos [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  La evaluación de expresiones asincrónicas requiere la implementación de la interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) y sus métodos [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[y GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Los eventos sincrónicos requieren la implementación del método [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Para que el motor escriba una salida de estilo cadena, debe implementar el método [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>Consulte también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
