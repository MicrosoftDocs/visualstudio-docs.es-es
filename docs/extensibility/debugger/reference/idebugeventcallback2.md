---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es utilizada por el motor de depuración \(DE\) para enviar eventos de depuración al administrador de depuración de la sesión \(SDM\).  
  
## Sintaxis  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## Notas para los implementadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa esta interfaz para recibir los eventos de un motor de depuración.  
  
## Notas para los llamadores  
 Un motor de depuración recibe normalmente esta interfaz cuando el SDM llama [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  Un motor de depuración envía el evento SDM llamando a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugEventCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía notificación de eventos de depuración al SDM.|  
  
## Comentarios  
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especifican que toman una interfaz de `IDebugEventCallback2` , éste no es el caso, y el puntero de interfaz siempre será un valor NULL.  En su lugar, el motor de depuración debe utilizar la interfaz de `IDebugEventCallback2` recibida en la llamada a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), a [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si un paquete implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, se recomienda encarecidamente que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> se invoca en distintas interfaces que se pasan a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)