---
title: IDebugPendingBreakpoint2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a53bf4dc987b597ffd28b54be0614bd967d07970
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845439"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Esta interfaz representa un punto de interrupción que está listo para enlazar a una ubicación del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto de interrupción pendiente desde un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfaz. Una llamada a [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea un `IDebugBreakpoint2` interfaz que representa un punto de interrupción enlazado en el programa.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugPendingBreakpoint2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si este punto de interrupción pendiente puede enlazar a una ubicación del código.|  
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Este punto de interrupción pendiente se enlaza a una o varias ubicaciones del código.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de este pendiente de punto de interrupción.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción que se usó para crear este punto de interrupción pendiente.|  
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna el estado virtualizado de este pendiente de punto de interrupción.|  
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de este pendiente de punto de interrupción.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Establece o cambia la condición asociada a este pendiente de punto de interrupción.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Establece o cambia el recuento de pass asociado a este pendiente de punto de interrupción.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos los puntos de interrupción enlazados desde este punto de interrupción pendiente.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos los puntos de interrupción de error que dan como resultado de este punto de interrupción pendiente.|  
|[Eliminar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina este punto de interrupción pendiente y todos los puntos de interrupción enlazados a partir de él.|  
  
## <a name="remarks"></a>Comentarios  
 `IDebugPendingBreakpoint2` puede considerarse como un proveedor de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o varios programas.  
  
 Un punto de interrupción pendiente puede producir potencialmente más de un punto de interrupción enlazado. Por ejemplo, un punto de interrupción en una plantilla de estilo de C++ podría producir un punto de interrupción enlazado para cada instancia única de esa plantilla.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)