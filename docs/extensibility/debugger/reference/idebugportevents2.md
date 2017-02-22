---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "Interfaz IDebugPortEvents2"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz notifica a un agente de escucha \(normalmente el administrador de depuración de sesión \[SDM\] o un motor de depuración\) del proceso y creación y destrucción de programa en un puerto determinado.  Esta información se puede utilizar para mostrar una vista en tiempo real de los procesos y los programas que se ejecutan en el puerto.  
  
## Sintaxis  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## Notas para los implementadores  
 Visual Studio implementará normalmente esta interfaz para recibir notificaciones sobre la creación y destrucción de programa.  Un motor de depuración puede implementar esta interfaz para escuchar estos eventos de puerto.  
  
## Notas para los llamadores  
 Todas las interfaces de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) se pueden consultar una interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> .  El método de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> para `IDebugPortEvents2` se denomina en la interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> para obtener una interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> .  finalmente, el método de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> en la interfaz de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> se denomina para enviar los eventos con el método de [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) .  
  
## métodos en el orden de Vtable  
 La siguiente tabla se muestra el método de `IDebugPortEvents2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envía los eventos que describen la creación y destrucción de procesos y de programas en el puerto.|  
  
## Comentarios  
 `IDebugPortEvents2` también usa el SDM a los programas de depuración que se ejecutan en un proceso que se está depurando ya.  
  
 Los eventos de puerto se pasan al SDM por esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)