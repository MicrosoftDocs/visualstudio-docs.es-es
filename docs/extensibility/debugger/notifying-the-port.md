---
title: "Notificar el puerto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puertos de notificación"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Notificar el puerto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Después de iniciar un programa, el puerto debe ser una notificación, como sigue:  
  
1.  Cuando un puerto recibe un nuevo nodo de programa, envía un evento de creación de programa a la sesión de depuración.  El evento contiene con él una interfaz que representa el programa.  
  
2.  Las consultas de la sesión de depuración el programa para el identificador de un motor de depuración al \(DE\) que puede adjuntar.  
  
3.  Las comprobaciones de la sesión de depuración para ver si el OF está en la lista de DES permitido para ese programa.  La sesión de depuración obtiene esta lista de los valores de programa de soluciones activa, pasados originalmente a ella por el paquete de depuración.  
  
     El OF debe estar en la lista permitido, o bien el OF no se adjuntará al programa.  
  
 Mediante programación, cuando un puerto primero recibe un nuevo nodo de programa, crea una interfaz de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) para representar el programa.  
  
> [!NOTE]
>  Esto no se debe confundir con la interfaz de `IDebugProgram2` creada más adelante con el motor de depuración \(DE\).  
  
 El puerto envía un evento de creación de programa de [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para el administrador \(SDM\) de depuración de sesión mediante una interfaz COM de `IConnectionPoint` .  
  
> [!NOTE]
>  Esto no se debe confundir con la interfaz de `IDebugProgramCreateEvent2` , que es enviada más adelante con el OF.  
  
 Junto con la propia interfaz de eventos, el puerto envía las interfaces de [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), de [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), y de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , que representan el puerto, el proceso, y el programa, respectivamente.  El SDM llama [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obtener el GUID de que puede depurar el programa.  GUID se obtuvo originalmente de la interfaz de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
 Las comprobaciones de SDM para ver si el OF está en la lista de DES permitido.  El SDM obtiene esta lista de los valores de programa de soluciones activa, pasados originalmente el paquete de depuración.  El OF debe estar en la lista permitido, o bien no se adjuntará al programa.  
  
 La identidad de se conoce una vez, el SDM está lista para adjuntarlo al programa.  
  
## Vea también  
 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)   
 [Asociar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)