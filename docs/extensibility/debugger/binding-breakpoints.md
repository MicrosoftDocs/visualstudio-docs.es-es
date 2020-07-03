---
title: Enlazar puntos de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903235"
---
# <a name="bind-breakpoints"></a>Enlazar puntos de interrupción
Si el usuario establece un punto de interrupción, quizás presionando **F9**, el IDE formula la solicitud y solicita la sesión de depuración para crear el punto de interrupción.

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción
 Establecer un punto de interrupción es un proceso de dos pasos, ya que es posible que el código o los datos afectados por el punto de interrupción no estén todavía disponibles. En primer lugar, se debe describir el punto de interrupción y, a continuación, cuando el código o los datos estén disponibles, se debe enlazar a ese código o datos, como se indica a continuación:

1. El punto de interrupción se solicita desde los motores de depuración correspondientes (DEs) y, a continuación, el punto de interrupción se enlaza al código o a los datos a medida que están disponibles.

2. La solicitud de punto de interrupción se envía a la sesión de depuración, que la envía a todo el DEs relevante. Cualquier DE que elija controlar el punto de interrupción crea un punto DE interrupción pendiente correspondiente.

3. La sesión de depuración recopila los puntos de interrupción pendientes y los devuelve al paquete de depuración (el componente de depuración de Visual Studio).

4. El paquete de depuración solicita a la sesión de depuración que enlace el punto de interrupción pendiente al código o a los datos. La sesión de depuración envía esta solicitud a todos los DEs relevantes.

5. Si el DE puede enlazar el punto de interrupción, devuelve un evento enlazado de punto de interrupción a la sesión de depuración. En caso contrario, envía un evento de error de punto de interrupción.

## <a name="pending-breakpoints"></a>Puntos de interrupción pendientes
 Un punto de interrupción pendiente puede enlazar a varias ubicaciones de código. Por ejemplo, una línea de código fuente para una plantilla de C++ se puede enlazar a cada secuencia de código generada a partir de la plantilla. La sesión de depuración puede usar un evento enlazado de punto de interrupción para enumerar los contextos de código enlazados a un punto de interrupción en el momento en que se envió el evento. Más adelante se pueden enlazar más contextos de código, por lo que el DE puede enviar varios eventos enlazados de punto de interrupción para cada solicitud de enlace. Sin embargo, un DE solo debe enviar un evento DE ERROR DE punto DE interrupción por solicitud DE enlace.

## <a name="implementation"></a>Implementación
 Mediante programación, el paquete de depuración llama al administrador de depuración de sesión (SDM) y proporciona una interfaz [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que contiene una estructura [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) , que describe el punto de interrupción que se va a establecer. Aunque los puntos de interrupción pueden ser de muchas formas, se resuelven en última instancia en un código o contexto de datos.

 El SDM pasa esta llamada a cada pertinente DE mediante una llamada a su método [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) . Si el control decide controlar el punto de interrupción, crea y devuelve una interfaz [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) . El SDM recopila estas interfaces y las pasa de nuevo al paquete de depuración como una sola `IDebugPendingBreakpoint2` interfaz.

 Hasta ahora, no se ha generado ningún evento.

 A continuación, el paquete de depuración intenta enlazar el punto de interrupción pendiente al código o a los datos mediante una llamada a [BIND](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que se implementa mediante el método de.

 Si el punto de interrupción está enlazado, el DE envía una interfaz DE eventos [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) al paquete de depuración. El paquete de depuración usa esta interfaz para enumerar todos los contextos de código (o el contexto de datos único) enlazados al punto de interrupción llamando a [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que devuelve una o más interfaces [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) . La interfaz [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) devuelve una interfaz [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) y [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) devuelve un [BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Unión que contiene el código o el contexto de datos.

 Si no puede enlazar el punto de interrupción, envía una sola interfaz de eventos [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al paquete de depuración. El paquete de depuración recupera el tipo de error (error o advertencia) y el mensaje informativo llamando a [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md), seguido de [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) y [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Esto devuelve un [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura que contiene el tipo de error y el mensaje.

 Si un control controla un punto de interrupción pero no puede enlazarlo, devuelve un error de tipo `BPET_TYPE_ERROR` . El paquete de depuración responde mostrando un cuadro de diálogo de error y el IDE coloca un glifo de exclamación dentro del glifo del punto de interrupción a la izquierda de la línea de código fuente.

 Si un control DE controla un punto de interrupción, no puede enlazarlo, pero otro DE puede enlazarlo, devuelve una advertencia. El IDE responde colocando un glifo de pregunta dentro del glifo de punto de interrupción a la izquierda de la línea de código fuente.

## <a name="see-also"></a>Vea también
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
