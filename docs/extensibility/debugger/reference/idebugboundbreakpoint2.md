---
title: IDebugBoundBreakpoint2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2
helpviewer_keywords: IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2322b548106a7cbfff5ca4d96d7fc2d317308b10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Esta interfaz representa un punto de interrupción que está enlazado a una ubicación del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea esta interfaz. Las llamadas a [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) y [siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) también se puede obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBoundBreakpoint2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente desde la que se creó el punto de interrupción enlazado especificado.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de este punto de interrupción enlazado.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtiene el número de llamadas actual para este punto de interrupción enlazado.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de punto de interrupción que describe este punto de interrupción.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita el punto de interrupción.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Establece el número de llamadas para este punto de interrupción enlazado.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Establece o cambia la condición asociada a este punto de interrupción enlazado.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Establece o cambiar el número de paso asociado a este punto de interrupción enlazado.|  
|[Eliminar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina el punto de interrupción.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)