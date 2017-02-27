---
title: "IDebugBoundBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2"
helpviewer_keywords: 
  - "Interfaz IDebugBoundBreakpoint2"
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un punto de interrupción que se enlaza a una ubicación del código.  
  
## Sintaxis  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz como parte de su compatibilidad para los puntos de interrupción.  
  
## Notas para los llamadores  
 una llamada a [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea esta interfaz.  Las llamadas a [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) y [Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) también pueden obtener la interfaz de This.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugBoundBreakpoint2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente de que el punto de interrupción enlazado especificado se creó.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de esto limitan el punto de interrupción.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtiene el número de llamadas actual para esto limitan el punto de interrupción.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de punto de interrupción que describe este punto de interrupción.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita el punto de interrupción.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Establece el número de llamadas para esto limitan el punto de interrupción.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Establece o cambia la condición asociado a este punto de interrupción enlazado.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Establece o cambia el recuento del paso asociado a este punto de interrupción enlazado.|  
|[Eliminar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Elimina el punto de interrupción.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)