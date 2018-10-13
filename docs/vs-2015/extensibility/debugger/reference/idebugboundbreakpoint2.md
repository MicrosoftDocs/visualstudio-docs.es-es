---
title: IDebugBoundBreakpoint2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 43d7bd42e025ef5ee36fca51f9a7b78ece94f130
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304536"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un punto de interrupción que está enlazado a una ubicación del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea esta interfaz. Las llamadas a [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) y [siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) también se puede obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBoundBreakpoint2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente desde la que se creó el punto de interrupción enlazado especificado.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de este punto de interrupción enlazado.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtiene el número de llamadas actual para este punto de interrupción enlazado.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de punto de interrupción que se describe en este punto de interrupción.|  
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita el punto de interrupción.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Establece el número de llamadas para este punto de interrupción enlazado.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Establece o cambia la condición asociada a este punto de interrupción enlazado.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Establece o cambiar el recuento de pass asociado a este punto de interrupción enlazado.|  
|[Eliminar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina el punto de interrupción.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

