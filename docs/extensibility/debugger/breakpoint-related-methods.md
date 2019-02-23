---
title: Métodos relacionados con el punto de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd40ac13cf00db2903f9c9dca7cf154572e2b81
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711181"
---
# <a name="breakpoint-related-methods"></a>Métodos relacionados con el punto de interrupción
Un motor de depuración (DE) debe admitir la configuración de puntos de interrupción. Depuración de Visual Studio admite los siguientes tipos de puntos de interrupción:

-   Enlazado

     Solicita a través de la interfaz de usuario y enlazar correctamente a una ubicación del código especificado

-   Pendiente

     Solicita a través de la interfaz de usuario pero no está enlazado a actual aún instrucciones

## <a name="discussion"></a>Discusión
 Por ejemplo, un punto de interrupción pendiente tiene lugar cuando las instrucciones no se han cargado. Cuando se carga el código pendiente try de puntos de interrupción para enlazar al código en la ubicación recomendada, es decir, para insertar las instrucciones de salto en el código. Los eventos se envían al administrador de depuración de sesión (SDM) para indicar el enlace correcto o para notificar a la que se produjeron errores de enlace.

 Un punto de interrupción pendiente también administra su propia lista interna de puntos de interrupción enlazados correspondientes. Una pendiente de punto de interrupción puede provocar la inserción de muchos de los puntos de interrupción en el código. La depuración de interfaz de usuario de Visual Studio muestra una vista de árbol de puntos de interrupción pendientes y sus correspondientes puntos de interrupción enlazados.

 Creación y uso de puntos de interrupción pendientes requieren la implementación de la [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) método, así como los métodos siguientes de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaces.

|Método|Descripción|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si un pendiente de punto de interrupción, puede enlazar a una ubicación del código.|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza un especificado pendiente de punto de interrupción a una o varias ubicaciones de código.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción pendiente.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción utilizada para crear un punto de interrupción pendiente.|
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de un punto de interrupción pendiente.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos los puntos de interrupción enlazados desde un punto de interrupción pendiente.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos los puntos de interrupción de error que se derivan de un punto de interrupción pendiente.|
|[Eliminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto de interrupción pendiente y todos los puntos de interrupción enlazados a partir de él.|

 Para enumerar los puntos de interrupción enlazados y puntos de interrupción de error, debe implementar todos los métodos de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) y de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Pendiente de los puntos de interrupción que se enlazan a un código ubicación requieren la implementación de las siguientes acciones [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) métodos.

|Método|Descripción|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que contiene un punto de interrupción.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción enlazado.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de punto de interrupción que describe un punto de interrupción.|
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita un punto de interrupción.|
|[Eliminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto de interrupción enlazado.|

 Resolución y solicitar información requieren la implementación de las siguientes acciones [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) métodos.

|Método|Descripción|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo del punto de interrupción representado por una resolución.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de punto de interrupción que describe un punto de interrupción.|

 Resolución de errores que pueden producirse durante el enlace requiere la implementación de las siguientes acciones [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) métodos.

|Método|Descripción|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que contiene un punto de interrupción de error.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de errores de punto de interrupción que describe un punto de interrupción de error.|

 Resolución de errores que pueden producirse durante el enlace también requiere los siguientes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Método|Descripción|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo de punto de interrupción.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de un punto de interrupción.|

 Ver el código fuente en un punto de interrupción, deberá implementar los métodos de [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) o los métodos de [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vea también
- [Evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md)