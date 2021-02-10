---
title: Tipos de eventos admitidos | Microsoft Docs
description: Obtenga información sobre los tipos de eventos que admite la depuración de Visual Studio, incluidos eventos asincrónicos, eventos sincrónicos y detención de eventos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9bf2e154d5803324161e073edbd74e049c0897ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960694"
---
# <a name="supported-event-types"></a>Tipos de eventos admitidos
La depuración de Visual Studio admite actualmente los siguientes tipos de eventos:

- Eventos asincrónicos

   Notifique al administrador de depuración de la sesión (SDM) y al IDE que está cambiando el estado de la aplicación que se está depurando. Estos eventos se procesan en el momento en que el SDM y el IDE. No se envía ninguna respuesta al motor DE depuración (DE) una vez que se procesa el evento. Las interfaces [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) y [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) son ejemplos de eventos asincrónicos.

- Eventos sincrónicos

   Notifique al SDM e IDE que está cambiando el estado de la aplicación que se está depurando. La única diferencia entre estos eventos y los eventos asincrónicos es que una respuesta se envía por medio del método [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

   El envío de un evento sincrónico es útil si necesita que su DE continúe el procesamiento después de que el IDE reciba y procese el evento.

- Eventos de detención sincrónica o detención de eventos

   Notifique al SDM y al IDE que la aplicación que se está depurando ha dejado de ejecutar el código. Cuando se envía un evento de detención por medio del [evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md)de método, se requiere el parámetro [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) . La detención de eventos se continúa mediante una llamada a uno de los métodos siguientes:

  - [Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de detención de eventos.

  > [!NOTE]
  > No se admiten eventos de detención asincrónica. Es un error enviar un evento de detención asincrónica.

## <a name="discussion"></a>Debate
 La implementación real de eventos depende del diseño de de. El tipo de cada evento enviado viene determinado por sus atributos, que se establecen al diseñar la DE. Por ejemplo, uno DE ellos puede enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como un evento asincrónico, mientras que otro puede enviarlo como un evento de detención.

 En la tabla siguiente se especifica qué parámetros de programa y de subproceso son necesarios para los eventos, así como los tipos de evento. Los eventos pueden ser sincrónicos. No es necesario que los eventos sean sincrónicos.

> [!NOTE]
> La interfaz [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) es necesaria para todos los eventos.

|Evento|IDebugProgram2|IDebugThread2|Detener eventos|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|No permitido|No permitido|No|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|No permitido|No permitido|No|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|Puede ser|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|Puede ser|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|Puede ser|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatorio|Permitido, pero no obligatorio|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatorio|Permitido, pero no obligatorio|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatorio|Permitido, pero no obligatorio|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatorio|Permitido, pero no obligatorio|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatorio|Permitido, pero no obligatorio|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|IDebugStopCompleteEvent2|Obligatorio|Obligatorio|Sí|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatorio|Obligatorio|Sí|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatorio|Obligatorio|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Permitido, pero no obligatorio|Permitido, pero no obligatorio|No|

## <a name="see-also"></a>Consulte también
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
