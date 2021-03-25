---
description: Esta interfaz representa un punto de interrupción que está listo para enlazarse a una ubicación del código.
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a52856cfa70491b7a7daa9079c111b1430475d22
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053716"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Esta interfaz representa un punto de interrupción que está listo para enlazarse a una ubicación del código.

## <a name="syntax"></a>Sintaxis

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto de interrupción pendiente a partir de una interfaz [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Una llamada a [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea una `IDebugBreakpoint2` interfaz que representa un punto de interrupción enlazado en el programa.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugPendingBreakpoint2` .

|Método|Descripción|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si este punto de interrupción pendiente puede enlazarse a una ubicación de código.|
|[Volver](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza este punto de interrupción pendiente a una o varias ubicaciones de código.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de este punto de interrupción pendiente.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción que se usó para crear este punto de interrupción pendiente.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna el estado virtualizado de este punto de interrupción pendiente.|
|[Habilitar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de este punto de interrupción pendiente.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Establece o cambia la condición asociada a este punto de interrupción pendiente.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Establece o cambia el número de pasos asociado a este punto de interrupción pendiente.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos los puntos de interrupción enlazados desde este punto de interrupción pendiente.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos los puntos de interrupción de error resultantes de este punto de interrupción pendiente.|
|[Eliminar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina este punto de interrupción pendiente y todos los puntos de interrupción enlazados a él.|

## <a name="remarks"></a>Observaciones
 `IDebugPendingBreakpoint2` puede considerarse como un proveedor de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o varios programas.

 Un punto de interrupción pendiente puede producir más de un punto de interrupción enlazado. Por ejemplo, un punto de interrupción en una plantilla de estilo C++ podría producir un punto de interrupción enlazado para cada instancia única de esa plantilla.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
