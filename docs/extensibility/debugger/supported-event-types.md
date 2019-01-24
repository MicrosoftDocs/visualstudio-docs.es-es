---
title: Admite los tipos de evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fc11158987ecb1d7401f1127318138c0b865f96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901797"
---
# <a name="supported-event-types"></a>Tipos de evento compatibles
Depuración de Visual Studio admite actualmente los siguientes tipos de evento:  
  
- Eventos asincrónicos  
  
   Notificar al administrador de depuración de la sesión (SDM) y el IDE que cambia el estado de la aplicación que se está depurando. Estos eventos se procesan en el tiempo libre del SDM y el IDE. No se envía al motor de depuración (DE) una vez que se procesa el evento. El [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) y [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfaces son ejemplos de eventos asincrónicos.  
  
- Eventos sincrónicos  
  
   Notificar el SDM y el IDE que cambia el estado de la aplicación que se está depurando. La única diferencia entre estos eventos y eventos asincrónicos es que se envía una respuesta por medio de la [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.  
  
   Enviar un evento sincrónico es útil si necesita que el DE continuar con el procesamiento después de que el IDE recibe y procesa el evento.  
  
- Los eventos de parada sincrónica o los eventos de parada  
  
   Notificar el SDM y el IDE que la aplicación que se está depura ha detenido la ejecución de código. Al enviar un evento de detención por medio del método [eventos](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) el parámetro es obligatorio. Detener eventos continúan mediante una llamada a uno de los métodos siguientes:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de detención.  
  
  > [!NOTE]
  >  No se admiten los eventos de detención asincrónica. Es un error al enviar un evento de detención asincrónica.  
  
## <a name="discussion"></a>Explicación  
 La implementación real de los eventos depende del diseño de la DE. El tipo de cada evento enviado viene determinada por sus atributos, que se establecen cuando se diseña la DE. Por ejemplo, puede enviar uno DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como un evento asincrónico, mientras que otro puede enviar como un evento de detención.  
  
 En la tabla siguiente especifica qué parámetros de programa y subproceso son necesarios para los eventos, así como tipos de eventos. Cualquier evento puede ser sincrónico. Ningún evento debe ser sincrónico.  
  
> [!NOTE]
>  El [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaz es necesaria para todos los eventos.  
  
|evento|IDebugProgram2|IDebugThread2|Los eventos de parada|  
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
  
## <a name="see-also"></a>Vea también  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)