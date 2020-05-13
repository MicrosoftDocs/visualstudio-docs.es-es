---
title: Eventos de Control (Control De Eventos) Microsoft Docs
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
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739086"
---
# <a name="control-events"></a>Eventos de control
Debe enviar eventos durante la ejecución controlada del programa. Todos los eventos se envían mediante el [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) interfaz y tienen atributos que requieren implementar el [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) método.

## <a name="additional-methods"></a>Métodos adicionales
 Algunos eventos requieren la implementación de métodos adicionales, como se indica a continuación:

- Enviar el [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaz cuando se inicializa el motor de depuración (DE) requiere que implemente el [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) método.

- El control de ejecución requiere la implementación de eventos de control como el [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) y[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaces. **IDebugBreakEvent2** solo es necesario para los saltos asincrónicos.

- Paso a paso en funciones requiere la implementación de la [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaz y sus métodos.

  Los eventos derivados de puntos de interrupción requieren la implementación de las interfaces [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)y [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) así como los métodos [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) y [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  La evaluación de expresiones asincrónicas requiere que implemente la interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) y sus métodos [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[y GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Los eventos sincrónicos requieren la implementación de la [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.

  Para que el motor escriba la salida de estilo de cadena, debe implementar el [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) método.

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
