---
title: "Enlazar puntos de interrupci&#243;n | Microsoft Docs"
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
  - "puntos de interrupción, enlace"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Enlazar puntos de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si el usuario establece un punto de interrupción, quizás presione F9, el IDE formulan la solicitud y pide confirmación para la sesión de depuración crear el punto de interrupción.  
  
## establecer un punto de interrupción  
 Establecer un punto de interrupción es un proceso de dos pasos, porque el código o los datos afectados por el punto de interrupción no podría estar disponible.  Primero, el punto de interrupción debería describirse y, a continuación, como el código o los datos disponible, debe estar enlazado a ese código o datos, como sigue:  
  
1.  El punto de interrupción se solicita a los motores pertinentes de \(DEs\) depuración, y el punto de interrupción se enlaza al código o los datos mientras está disponible.  
  
2.  La solicitud de punto de interrupción se envía a la sesión de depuración, que la envía a todo el DES pertinente.  Cualquier OF que elija para controlar el punto de interrupción crea un correspondiente hasta que finalice el punto de interrupción.  
  
3.  La sesión de depuración recopila los puntos de interrupción pendientes y los devuelve al paquete de depuración \(el componente de depuración de Visual Studio\).  
  
4.  El paquete de depuración pide a la sesión de depuración enlazar el punto de interrupción pendiente en el código o en los datos.  La sesión de depuración envía esta solicitud a todo el DES pertinente.  
  
5.  Si el OF puede enlazar el punto de interrupción, envía un punto de interrupción evento enlazado a la sesión de depuración.  Si no, envía un evento de error de punto de interrupción en su lugar.  
  
## Pendientes los puntos de interrupción  
 Un punto de interrupción pendiente puede enlazar a las varias ubicaciones del código.  Por ejemplo, una línea de código fuente de la plantilla de c\+\+. puede enlazar a cada secuencia de código generado de la plantilla.  La sesión de depuración se puede utilizar un evento enlazado de puntos de interrupción para enumerar los contextos de código enlazados a un punto de interrupción cuando el evento se envió.  Más contextos de código se pueden enlazar más adelante, por lo que el OF puede enviar punto de interrupción varios eventos enlazados para cada solicitud de enlace.  Sin embargo, un OF debe enviar sólo un evento de error de punto de interrupción por solicitud de enlace.  
  
## Implementación  
 Mediante programación, el paquete de depuración llama al administrador de depuración de la sesión \(SDM\) y proporciona una interfaz de [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que contenga una estructura de [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) , que describe el punto de interrupción que se establecerá.  Aunque los puntos de interrupción pueden ser de varios formularios, resuelva finalmente a un contexto de código o de los datos.  
  
 El SDM pasa esta llamada a cada OF pertinente llamando a su método de [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) .  Si el OF elija para controlar el punto de interrupción, crea y devuelve una interfaz de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  El SDM obtiene estas interfaces y los devuelve al paquete de depuración como una interfaz de `IDebugPendingBreakpoint2` .  
  
 Hasta ahora, no se ha generado ningún evento.  
  
 El paquete de depuración después intenta enlazar el punto de interrupción pendiente en el código o en los datos llamando a [Enlazar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), implementado por el OF.  
  
 Si se enlaza el punto de interrupción, el OF envía una interfaz de eventos de [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) al paquete de depuración.  El paquete de depuración utiliza esta interfaz para mostrar todos los contextos de código \(o el mismo contexto de datos\) enlazados al punto de interrupción llamando a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que devuelve una o más interfaces de [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  La interfaz de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) devuelve una interfaz de [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) , y [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) devuelve una combinación de [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) que contiene el contexto del código o de los datos.  
  
 Si el OF no puede enlazar el punto de interrupción, envía una sola interfaz de eventos de [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al paquete de depuración.  El paquete de depuración recupera el tipo de error \(error o advertencia\) y el mensaje informativo llamando a [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido por [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) y [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md).  Esto devuelve una estructura de [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) que contiene el tipo y el mensaje de error.  
  
 Si un OF controla un punto de interrupción pero no puede enlazarlo, devuelve un error de `BPET_TYPE_ERROR`escrito.  El paquete de depuración responde muestra un cuadro de diálogo de error, y el IDE coloca un glifo de exclamación dentro del glifo del punto de interrupción a la izquierda de la línea de código fuente.  
  
 Si un OF controla un punto de interrupción, no puede enlazarlo, pero otra persona OF puede enlazarlo, se devuelve una advertencia.  El IDE responde colocando un glifo question dentro del glifo del punto de interrupción a la izquierda de la línea de código fuente.  
  
## Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)