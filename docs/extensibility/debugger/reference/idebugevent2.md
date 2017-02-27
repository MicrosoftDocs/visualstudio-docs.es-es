---
title: "IDebugEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugEvent2"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se utiliza para comunicar la información de depuración crítica, como detener en un punto de interrupción, y la información no crítica, como un mensaje de depuración.  
  
## Sintaxis  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) y el proveedor del puerto de personalizados implementan esta interfaz en el mismo objeto que el resto de las interfaces de eventos.  
  
## Notas para los llamadores  
 Utilizando el argumento de identificador de interfaz \(IID\) especificado a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o a [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), las llamadas [QueryInterface](/visual-cpp/atl/queryinterface) de administrador \(SDM\) de depuración de sesión en la interfaz de `IDebugEvent2` para obtener la interfaz adecuada del evento.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos para este evento de depuración.|  
  
## Comentarios  
 Varias interfaces de eventos, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no se derivan de la interfaz IDebugEvent2 sino que se implementan como una interfaz diferente en el mismo objeto que `IDebugEvent2`.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)