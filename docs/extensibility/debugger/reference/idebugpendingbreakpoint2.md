---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "Interfaz IDebugPendingBreakpoint2"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un punto de interrupción que esté listo para enlazar a una ubicación del código.  
  
## Sintaxis  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz como parte de su compatibilidad para los puntos de interrupción.  
  
## Notas para los llamadores  
 una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto de interrupción pendiente de una interfaz de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) .  Una llamada a [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea una interfaz de `IDebugBreakpoint2` que representa un punto de interrupción enlazado en el programa.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugPendingBreakpoint2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si este punto de interrupción pendiente puede enlazar a una ubicación del código.|  
|[Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza este punto de interrupción pendiente a una o varias ubicaciones del código.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de este punto de interrupción pendiente.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción que se utilizó para crear este punto de interrupción pendiente.|  
|[Virtualizar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alterna el estado virtualizados de este punto de interrupción pendiente.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de este punto de interrupción pendiente.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Establece o cambia la condición asociado a este punto de interrupción pendiente.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Establece o cambia el recuento de paso asociado a este punto de interrupción pendiente.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Muestra todos los puntos de interrupción enlazados de este punto de interrupción pendiente.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Muestra todos los puntos de interrupción de error resultantes de este punto de interrupción pendiente.|  
|[Eliminar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina este punto de interrupción pendiente y todos los puntos de interrupción enlazados de.|  
  
## Comentarios  
 `IDebugPendingBreakpoint2` se puede considerar como proveedor de toda la información necesaria para enlazar un punto de interrupción al código que se puede aplicar a uno o a muchos programas.  
  
 Un punto de interrupción pendiente podría mostrar más de un punto de interrupción enlazado.  Por ejemplo, un punto de interrupción en plantillas de C\+\+. \+\+\-style podría mostrar un punto de interrupción enlazado para cada instancia única de esa plantilla.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)