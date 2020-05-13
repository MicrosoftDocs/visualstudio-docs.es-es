---
title: Tipos de eventos admitidos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712800"
---
# <a name="supported-event-types"></a>Tipos de eventos admitidos
La depuración de Visual Studio admite actualmente los siguientes tipos de eventos:

- Eventos asincrónicos

   Notifique al administrador de depuración de sesión (SDM) y al IDE que el estado de la aplicación que se está depurando está cambiando. Estos eventos se procesan en el tiempo libre del SDM y el IDE. No se envía ninguna respuesta al motor de depuración (DE) una vez que se procesa el evento. Las interfaces [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) son ejemplos de eventos asincrónicos.

- Eventos sincrónicos

   Notifique al SDM y al IDE que el estado de la aplicación que se está depurando está cambiando. La única diferencia entre estos eventos y eventos asincrónicos es que se envía una respuesta mediante el método [ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   Enviar un evento sincrónico es útil si necesita que su DE continúe el procesamiento después de que el IDE reciba y procese el evento.

- Eventos de detención sincrónicos o eventos de detención

   Notifique al SDM y al IDE que la aplicación que se está depurando ha dejado de ejecutar código. Cuando se envía un evento de detención mediante el método [Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md), se requiere el parámetro [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) . Los eventos de detención se continúan mediante una llamada a uno de los métodos siguientes:

  - [Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de detener eventos.

  > [!NOTE]
  > No se admiten eventos de detención asincrónicos. Es un error enviar un evento de detención asincrónico.

## <a name="discussion"></a>Discusión
 La implementación real de eventos depende del diseño de su DE. El tipo de cada evento enviado viene determinado por sus atributos, que se establecen al diseñar la DE. Por ejemplo, un DE puede enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como un evento asincrónico, mientras que otro puede enviarlo como un evento de detención.

 En la tabla siguiente se especifica qué parámetros de programa y subproceso son necesarios para qué eventos, así como tipos de eventos. Cualquier evento puede ser sincrónico. Ningún evento debe ser sincrónico.

> [!NOTE]
> El [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaz es necesaria para todos los eventos.

|Evento|IDebugProgram2|IDebugThread2|Detener eventos|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|No permitida|No permitida|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|No permitida|No permitida|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|Puede ser|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|Puede ser|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|Puede ser|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatorio|Permitido, pero no requerido|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatorio|Permitido, pero no requerido|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatorio|Permitido, pero no requerido|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatorio|Permitido, pero no requerido|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatorio|Permitido, pero no requerido|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|IDebugStopCompleteEvent2|Obligatorio|Obligatorio|Sí|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Permitido, pero no requerido|Permitido, pero no requerido|No|

## <a name="see-also"></a>Vea también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
