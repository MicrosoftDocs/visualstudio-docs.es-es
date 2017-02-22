---
title: "Tipos de evento compatible | Microsoft Docs"
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
  - "depurar [SDK de depuración], admite eventos"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Tipos de evento compatible
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio depura actualmente admite los tipos de evento siguientes:  
  
-   eventos asincrónicos  
  
     Notifique al administrador y el \(SDM\) IDE de depuración de sesión que el estado de la aplicación que es depurados está cambiando.  Estos eventos se procesan en el cuando desee de SDM y del IDE.  No se envía ninguna respuesta al motor \(DE\) de depuración cuando se procesa el evento.  las interfaces de [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) y de [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) son ejemplos de eventos asincrónicos.  
  
-   eventos sincrónicos  
  
     Notifique al SDM y el IDE que el estado de la aplicación que es depurados está cambiando.  La única diferencia entre estos eventos y los eventos asincrónicos es que una respuesta se envía mediante el método de [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)  
  
     El envío de un evento sincrónico es útil si necesita el OF continúe procesando después del IDE recibe y procesa el evento.  
  
-   eventos que detienen sincrónicos, o detener eventos  
  
     Notifique al SDM y el IDE que la aplicación que se depure ha detenido la ejecución de código.  Cuando se envía un evento que detiene mediante el método [Evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md), se requiere el parámetro de [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) .  Los eventos de parada son continuados por una llamada a uno de los métodos siguientes:  
  
    -   [Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Paso](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de parada.  
  
    > [!NOTE]
    >  el asincrónico que detiene eventos no se admite.  es un error para enviar un evento que detiene asincrónico.  
  
## Explicación  
 La implementación real de eventos depende del diseño de.  Los atributos determina el tipo de cada evento enviado, que se establecen al diseñar el OF.  Por ejemplo, un OF puede enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como evento asincrónico, mientras que otro puede enviarlo como un evento que detiene.  
  
 La tabla siguiente especifica que los parámetros del programa y subprocesos necesarios para los que los eventos, así como los tipos de evento.  cualquier evento puede ser sincrónico.  ningún evento necesita ser sincrónico.  
  
> [!NOTE]
>  la interfaz de [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) se requiere para todos los eventos.  
  
|Evento|IDebugProgram2|IDebugThread2|Eventos de parada|  
|------------|--------------------|-------------------|-----------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|No se permite|No se permite|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|No se permite|No se permite|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|puede ser|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|puede ser|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|puede ser|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obligatorio|Permitido, aunque no necesario|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obligatorio|Permitido, aunque no necesario|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obligatorio|Permitido, aunque no necesario|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obligatorio|Permitido, aunque no necesario|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obligatorio|Permitido, aunque no necesario|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|IDebugStopCompleteEvent2|Obligatorio|Obligatorio|Sí|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obligatorio|Obligatorio|Sí|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obligatorio|Obligatorio|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Permitido, aunque no necesario|Permitido, aunque no necesario|No|  
  
## Vea también  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)