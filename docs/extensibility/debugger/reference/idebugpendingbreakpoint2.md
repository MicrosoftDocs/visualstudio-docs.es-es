---
title: IDebugPendingBreakpoint2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725641"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Esta interfaz representa un punto de interrupción que está listo para enlazarse a una ubicación de código.

## <a name="syntax"></a>Sintaxis

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto de interrupción pendiente desde un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaz. Una llamada [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) a `IDebugBreakpoint2` Bind crea una interfaz que representa un punto de interrupción enlazado en el programa.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugPendingBreakpoint2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si este punto de interrupción pendiente se puede enlazar a una ubicación de código.|
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza este punto de interrupción pendiente a una o varias ubicaciones de código.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de este punto de interrupción pendiente.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción que se usó para crear este punto de interrupción pendiente.|
|[Virtualizar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna el estado virtualizado de este punto de interrupción pendiente.|
|[Habilitar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de este punto de interrupción pendiente.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Establece o cambia la condición asociada a este punto de interrupción pendiente.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Establece o cambia el recuento de pasadas asociado a este punto de interrupción pendiente.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos los puntos de interrupción enlazados desde este punto de interrupción pendiente.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos los puntos de interrupción de error resultantes de este punto de interrupción pendiente.|
|[Eliminar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina este punto de interrupción pendiente y todos los puntos de interrupción enlazados desde él.|

## <a name="remarks"></a>Observaciones
 `IDebugPendingBreakpoint2`se puede considerar como un proveedor de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o varios programas.

 Un punto de interrupción pendiente puede producir potencialmente más de un punto de interrupción enlazado. Por ejemplo, un punto de interrupción en una plantilla de estilo C++podría producir un punto de interrupción enlazado para cada instancia única de esa plantilla.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
