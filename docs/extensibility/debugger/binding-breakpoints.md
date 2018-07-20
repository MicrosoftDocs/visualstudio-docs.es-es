---
title: Enlace de puntos de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e02b3da843f7e4cffe33d660a8a82ab3c4c0dc03
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153451"
---
# <a name="bind-breakpoints"></a>Enlazar los puntos de interrupción
Si el usuario establece un punto de interrupción, quizás presionando **F9**, el IDE se formule la solicitud y se solicita la sesión de depuración para crear el punto de interrupción.  
  
## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción  
 Establecer un punto de interrupción es un proceso en dos pasos, porque el código o los datos afectados por el punto de interrupción podrían no estar disponibles. En primer lugar, se debe describir el punto de interrupción y, a continuación, tal como están disponibles el código o datos, se debe estar enlazada a ese código o datos, como se indica a continuación:  
  
1.  El punto de interrupción se solicita desde los motores de depuración relevantes (DEs) y, a continuación, se enlaza el punto de interrupción en el código o datos cuando se encuentre disponible.  
  
2.  La solicitud de punto de interrupción se envía a la sesión de depuración, que lo envía a todos los DEs pertinentes. Cualquier DE que elige para controlar el punto de interrupción crea correspondiente pendiente de punto de interrupción.  
  
3.  La sesión de depuración recopila los puntos de interrupción pendientes y los envía al paquete de depuración (el componente de depuración de Visual Studio).  
  
4.  El paquete de depuración solicita la sesión de depuración para enlazar el punto de interrupción pendiente al código o datos. La sesión de depuración envía esta solicitud a todos los DEs pertinentes.  
  
5.  Si la DE se puede enlazar el punto de interrupción, envía que un punto de interrupción enlazado el evento a la sesión de depuración. Si no es así, envía un evento de error de punto de interrupción en su lugar.  
  
## <a name="pending-breakpoints"></a>Puntos de interrupción pendientes  
 Un punto de interrupción pendiente puede enlazar a varias ubicaciones del código. Por ejemplo, puede enlazar una línea de código fuente de una plantilla de C++ para cada secuencia de código generado a partir de la plantilla. La sesión de depuración puede usar un evento de punto de interrupción enlazado para enumerar los contextos de código enlazados a un punto de interrupción en el momento en que se envió el evento. Más contextos de código se pueden enlazar más adelante, por lo que puede enviar la DE que punto de interrupción varias enlaza eventos para cada solicitud de enlace. Sin embargo, a DE debe enviar un solo evento de error de punto de interrupción por solicitud de enlace.  
  
## <a name="implementation"></a>Implementación  
 Mediante programación, el paquete de depuración se llama a la depuración de la sesión manager (SDM) y le da un [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaz que encapsula un [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) estructura que describe el punto de interrupción debe establecerse. Aunque los puntos de interrupción pueden ser de muchas formas, resuelven en última instancia a un contexto de datos o código.  
  
 El SDM pasa esta llamada a cada relevantes DE mediante una llamada a su [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método. Si decide que la DE controlar el punto de interrupción, crea y devuelve un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz. El SDM recopila estas interfaces y los pasa al paquete de depuración como una sola `IDebugPendingBreakpoint2` interfaz.  
  
 Hasta ahora, se han generado ningún evento.  
  
 El paquete de depuración, a continuación, intenta enlazar el punto de interrupción pendiente a código o datos mediante una llamada a [enlazar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que es implementado por la DE.  
  
 Si el punto de interrupción enlazado, envía la DE un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaz de eventos para el paquete de depuración. Utiliza el paquete de depuración enlaza esta interfaz para enumerar todos los contextos de código (o el contexto de datos única) hasta el punto de interrupción mediante una llamada a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que devuelve uno o varios [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaces. El [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaz devuelve un [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz, y [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) devuelve un [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) unión que contiene el contexto de código o datos.  
  
 Si el DE es no se puede enlazar el punto de interrupción, envía un solo [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfaz de eventos para el paquete de depuración. El paquete de depuración recupera el tipo de error (error o advertencia) y el mensaje informativo mediante una llamada a [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) y [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Esto devuelve un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura que contiene el tipo de error y el mensaje.  
  
 Si a DE un punto de interrupción encarga pero no puede enlazar a él, devuelve un error de tipo `BPET_TYPE_ERROR`. El paquete de depuración responde al mostrar un cuadro de diálogo de error y el IDE coloca un glifo de signo de exclamación dentro el glifo de punto de interrupción a la izquierda de la línea de código fuente.  
  
 Si a DE controla un punto de interrupción, no se puede enlazar, pero algunos otros DE puede enlazarlo, devuelve una advertencia. El IDE responde mediante la colocación de un glifo de pregunta en el glifo de punto de interrupción a la izquierda de la línea de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)