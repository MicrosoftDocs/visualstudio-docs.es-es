---
title: Admite los tipos de evento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b308aabacf5a82f4ea630ccae256c56526f793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134391"
---
# <a name="supported-event-types"></a>Tipos de evento compatible
Depuración de Visual Studio admite actualmente los siguientes tipos de eventos:  
  
-   Eventos asincrónicos  
  
     Notificar el Administrador de sesión de depuración (SDM) y IDE que se está cambiando el estado de la aplicación que se está depurando. Estos eventos se procesan en el tiempo libre de lo SDM y el IDE. No hay respuesta se envía al motor de depuración (Alemania) una vez que se procesa el evento. El [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) y [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfaces son ejemplos de eventos asincrónicos.  
  
-   Eventos sincrónicos  
  
     Notificar el SDM y el IDE que se está cambiando el estado de la aplicación que se está depurando. La única diferencia entre estos eventos y eventos asincrónicos es que se envía una respuesta por medio de la [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.  
  
     Enviar un evento sincrónico es útil si necesita su Alemania para continuar el procesamiento después de que el IDE recibe y procesa el evento.  
  
-   Los eventos de parada sincrónico o los eventos de parada  
  
     Notificar el SDM y el IDE de que la aplicación que se está depura se ha detenido la ejecución de código. Cuando se envía un evento de detención por medio del método [eventos](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parámetro es obligatorio. Detener eventos continúan mediante una llamada a uno de los métodos siguientes:  
  
    -   [Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de detención.  
  
    > [!NOTE]
    >  No se admiten los eventos de detención asincrónica. Es un error al enviar un evento de detención asincrónica.  
  
## <a name="discussion"></a>Explicación  
 La implementación real de eventos depende del diseño de su Alemania. El tipo de cada evento que se envía es determinado por sus atributos, que se establecen cuando se diseña el Alemania. Por ejemplo, puede enviar una Alemania un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como evento asíncrono, mientras que otro puede enviar un evento de detención.  
  
 En la tabla siguiente especifica qué parámetros de programa y los subprocesos son necesarios para los eventos, así como los tipos de evento. Los eventos pueden ser sincrónicas. Ningún evento debe ser sincrónico.  
  
> [!NOTE]
>  El [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaz es necesaria para todos los eventos.  
  
|evento|IDebugProgram2|IDebugThread2|Los eventos de parada|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|No permitido|No permitido|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|No permitido|No permitido|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|Puede ser|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|Puede ser|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|Puede ser|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|IDebugStopCompleteEvent2|Obligatorio|Obligatorio|Sí|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Puede, pero no es obligatorio|Puede, pero no es obligatorio|No|  
  
## <a name="see-also"></a>Vea también  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)