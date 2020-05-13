---
title: Puntos de interrupción de enlace ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739229"
---
# <a name="bind-breakpoints"></a>Enlazar puntos de interrupción
Si el usuario establece un punto de interrupción, quizás presionando **F9**, el IDE formula la solicitud y solicita a la sesión de depuración que cree el punto de interrupción.

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción
 Establecer un punto de interrupción es un proceso de dos pasos, porque es posible que el código o los datos afectados por el punto de interrupción aún no estén disponibles. En primer lugar, se debe describir el punto de interrupción y, a continuación, a medida que el código o los datos estén disponibles, debe estar enlazado a ese código o datos, como se indica a continuación:

1. El punto de interrupción se solicita a los motores de depuración (DE) relevantes y, a continuación, el punto de interrupción se enlaza al código o a los datos a medida que esté disponible.

2. La solicitud de punto de interrupción se envía a la sesión de depuración, que la envía a todos los DE relevantes. Cualquier DE que elija controlar el punto de interrupción crea un punto de interrupción pendiente correspondiente.

3. La sesión de depuración recopila los puntos de interrupción pendientes y los devuelve al paquete de depuración (el componente de depuración de Visual Studio).

4. El paquete de depuración solicita a la sesión de depuración que enlace el punto de interrupción pendiente al código o a los datos. La sesión de depuración envía esta solicitud a todos los DE relevantes.

5. Si el DE puede enlazar el punto de interrupción, envía un evento enlazado de punto de interrupción a la sesión de depuración. Si no es así, envía un evento de error de punto de interrupción en su lugar.

## <a name="pending-breakpoints"></a>Puntos de interrupción pendientes
 Un punto de interrupción pendiente puede enlazarse a varias ubicaciones de código. Por ejemplo, una línea de código fuente para una plantilla C++ puede enlazarse a cada secuencia de código generada a partir de la plantilla. La sesión de depuración puede usar un evento enlazado a punto de interrupción para enumerar los contextos de código enlazados a un punto de interrupción en el momento en que se envió el evento. Más contextos de código se pueden enlazar más adelante, por lo que la DE puede enviar varios eventos enlazados de punto de interrupción para cada solicitud de enlace. Sin embargo, un DE debe enviar solo un evento de error de punto de interrupción por solicitud de enlace.

## <a name="implementation"></a>Implementación
 Mediante programación, el paquete de depuración llama al administrador de depuración de sesión (SDM) y le proporciona una interfaz [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que ajusta una estructura [BP_REQUEST_INFO,](../../extensibility/debugger/reference/bp-request-info.md) que describe el punto de interrupción que se va a establecer. Aunque los puntos de interrupción pueden ser de muchos formularios, en última instancia se resuelven en un contexto de código o datos.

 El SDM pasa esta llamada a cada DE relevante mediante una llamada a su [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método. Si el DE elige controlar el punto de interrupción, crea y devuelve un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaz. El SDM recoge estas interfaces y las pasa de `IDebugPendingBreakpoint2` nuevo al paquete de depuración como una sola interfaz.

 Hasta ahora, no se han generado eventos.

 A continuación, el paquete de depuración intenta enlazar el punto de interrupción pendiente al código o a los datos mediante una llamada a [Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que se implementa mediante la DE.

 Si el punto de interrupción está enlazado, el DE envía un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaz de eventos al paquete de depuración. El paquete de depuración utiliza esta interfaz para enumerar todos los contextos de código (o el contexto de datos único) enlazados al punto de interrupción mediante una llamada a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que devuelve una o varias [interfaces IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . El [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) interfaz devuelve un [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz y [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) devuelve un [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) unión que contiene el código o el contexto de datos.

 Si el DE no puede enlazar el punto de interrupción, envía una única interfaz de eventos [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al paquete de depuración. El paquete de depuración recupera el tipo de error (error o advertencia) y el mensaje informativo llamando a [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) y [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Esto devuelve una estructura [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) que contiene el tipo de error y el mensaje.

 Si un DE controla un punto de interrupción `BPET_TYPE_ERROR`pero no puede enlazarlo, devuelve un error de tipo . El paquete de depuración responde mostrando un cuadro de diálogo de error y el IDE coloca un glifo de exclamación dentro del glifo de punto de interrupción a la izquierda de la línea de código fuente.

 Si un DE controla un punto de interrupción, no puede enlazarlo, pero alguna otra DE podría enlazarlo, devuelve una advertencia. El IDE responde colocando un glifo de pregunta dentro del glifo de punto de interrupción a la izquierda de la línea de código fuente.

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
