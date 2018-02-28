---
title: "Enlace los puntos de interrupción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 55416d6b156055d967424476f5add3b4ed75d18d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="binding-breakpoints"></a>Puntos de interrupción de enlace
Si el usuario establece un punto de interrupción, quizás presionando F9, el IDE formula la solicitud y solicita la sesión de depuración para crear el punto de interrupción.  
  
## <a name="setting-a-breakpoint"></a>Establecer un punto de interrupción  
 Establecer un punto de interrupción es un proceso de dos pasos, porque el código o los datos afectados por el punto de interrupción podrían no estar disponibles. En primer lugar, el punto de interrupción se debe describir, y, a continuación, como código o datos deja de estar disponibles, se debe estar enlazado a ese código o datos, como se indica a continuación:  
  
1.  El punto de interrupción se solicita los motores de depuración relevantes (DEs) y, a continuación, el punto de interrupción está enlazado con el código o datos cuando se encuentre disponible.  
  
2.  La solicitud de punto de interrupción se envía a la sesión de depuración, que lo envía a todos los DEs relevante. Cualquier Alemania que elige para controlar el punto de interrupción crea su correspondiente pendiente de punto de interrupción.  
  
3.  La sesión de depuración recopila los puntos de interrupción pendientes y los envía al paquete de depuración (el componente de depuración de Visual Studio).  
  
4.  El paquete de depuración solicita la sesión de depuración para enlazar el punto de interrupción pendiente al código o datos. La sesión de depuración envía esta solicitud a todos los DEs relevante.  
  
5.  Si el Alemania puede enlazar el punto de interrupción, envía que un punto de interrupción enlazado eventos a la sesión de depuración. De lo contrario, envía un evento de error de punto de interrupción en su lugar.  
  
## <a name="pending-breakpoints"></a>Puntos de interrupción pendientes  
 Un punto de interrupción pendiente puede enlazar a varias ubicaciones de código. Por ejemplo, puede enlazar una línea de código fuente de una plantilla de C++ para cada secuencia de código generado a partir de la plantilla. La sesión de depuración puede usar un evento de enlace de punto de interrupción para enumerar los contextos de código enlazados a un punto de interrupción en el momento en que se envió el evento. Varios contextos de código se pueden enlazar más adelante, por lo que la DE puede enviar que varios puntos de interrupción enlazado los eventos para cada solicitud de enlace. Sin embargo, un Alemania debería enviar un solo evento de error de punto de interrupción por solicitud de enlace.  
  
## <a name="implementation"></a>Implementación  
 Mediante programación, el paquete de depuración llama la depuración de sesión de administrador (SDM) y le da un [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaz que contiene un [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) estructura que describe el punto de interrupción se puede establecer. Aunque los puntos de interrupción pueden ser de muchas formas, resuelven en última instancia a un contexto de código o datos.  
  
 El SDM pasa esta llamada a cada Alemania relevante mediante una llamada a su [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método. Si decide que la DE controlar el punto de interrupción, crea y devuelve un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz. El SDM recopila estas interfaces y los pasa al paquete de depuración como una sola `IDebugPendingBreakpoint2` interfaz.  
  
 Hasta ahora, no se ha generado ningún evento.  
  
 El paquete de depuración, a continuación, intenta enlazar el punto de interrupción pendiente al código o datos mediante una llamada a [enlazar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que se implementa mediante el Alemania.  
  
 Si se enlaza el punto de interrupción, envía la DE un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaz de eventos para el paquete de depuración. El paquete de depuración utiliza esta interfaz para enumerar todos los contextos de código (o en el contexto de datos única) enlazada al punto de interrupción mediante una llamada a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que devuelve uno o varios [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaces. El [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaz devuelve un [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz, y [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) devuelve un [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) unión que contiene el contexto de código o datos.  
  
 Si el DE es no se puede enlazar el punto de interrupción, envía una sola [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaz de eventos para el paquete de depuración. El paquete de depuración recupera el tipo de error (error o advertencia) y el mensaje informativo mediante una llamada a [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) y [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Esto devuelve un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura que contiene el tipo de error y el mensaje.  
  
 Si un Alemania controla un punto de interrupción, pero no puede enlazar a él, devuelve un error de tipo `BPET_TYPE_ERROR`. El paquete de depuración responde mostrando un cuadro de diálogo de error y el IDE coloca un glifo de signo de exclamación dentro el glifo de punto de interrupción a la izquierda de la línea de código fuente.  
  
 Si un Alemania administra un punto de interrupción, no se puede enlazar, pero algunos otros Alemania puede enlazarlo, devuelve una advertencia. El IDE responde colocando un glifo de la pregunta en el glifo de punto de interrupción a la izquierda de la línea de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)