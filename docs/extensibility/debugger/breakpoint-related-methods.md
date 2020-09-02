---
title: Métodos relacionados con los puntos de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739210"
---
# <a name="breakpoint-related-methods"></a>Métodos relacionados con los puntos de interrupción
Un motor de depuración (DE) debe admitir la configuración de puntos de interrupción. La depuración de Visual Studio admite los siguientes tipos de puntos de interrupción:

- Bound

     Solicitada a través de la interfaz de usuario y enlazada correctamente a una ubicación de código especificada

- Pendiente

     Solicitado a través de la interfaz de usuario, pero que aún no se ha enlazado a instrucciones reales

## <a name="discussion"></a>Debate
 Por ejemplo, se produce un punto de interrupción pendiente cuando las instrucciones aún no se han cargado. Cuando se carga el código, los puntos de interrupción pendientes intentan enlazarse con el código en la ubicación indicada, es decir, para insertar instrucciones de salto en el código. Los eventos se envían al administrador de depuración de la sesión (SDM) para indicar que el enlace se ha realizado correctamente o para notificar que hubo errores de enlace.

 Un punto de interrupción pendiente también administra su propia lista interna de puntos de interrupción enlazados correspondientes. Un punto de interrupción pendiente puede producir la inserción de muchos puntos de interrupción en el código. La interfaz de usuario de depuración de Visual Studio muestra una vista de árbol de los puntos de interrupción pendientes y sus puntos de interrupción enlazados correspondientes.

 La creación y el uso de puntos de interrupción pendientes requieren la implementación del método [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , así como de los siguientes métodos de las interfaces de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Método|Descripción|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si un punto de interrupción pendiente especificado puede enlazarse a una ubicación de código.|
|[Volver](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza un punto de interrupción pendiente especificado a una o varias ubicaciones de código.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción pendiente.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción utilizada para crear un punto de interrupción pendiente.|
|[Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de un punto de interrupción pendiente.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos los puntos de interrupción enlazados desde un punto de interrupción pendiente.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos los puntos de interrupción de error resultantes de un punto de interrupción pendiente.|
|[Eliminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto de interrupción pendiente y todos los puntos de interrupción enlazados a él.|

 Para enumerar los puntos de interrupción enlazados y los puntos de interrupción de error, debe implementar todos los métodos de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) y de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Los puntos de interrupción pendientes que se enlazan a una ubicación de código requieren la implementación de los siguientes métodos de [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

|Método|Descripción|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que contiene un punto de interrupción.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción enlazado.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución del punto de interrupción que describe un punto de interrupción.|
|[Habilitar](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita un punto de interrupción.|
|[Eliminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina un punto de interrupción enlazado.|

 La información de resolución y solicitud requiere la implementación de los siguientes métodos de [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .

|Método|Descripción|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo del punto de interrupción representado por una resolución.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución del punto de interrupción que describe un punto de interrupción.|

 La resolución de los errores que pueden producirse durante el enlace requiere la implementación de los siguientes métodos de [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

|Método|Descripción|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que contiene un punto de interrupción de error.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de errores de punto de interrupción que describe un punto de interrupción de error.|

 La resolución de los errores que pueden producirse durante el enlace también requiere los siguientes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Método|Descripción|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo de un punto de interrupción.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de un punto de interrupción.|

 La visualización del código fuente en un punto de interrupción requiere la implementación de los métodos de [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) y/o los métodos de [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
