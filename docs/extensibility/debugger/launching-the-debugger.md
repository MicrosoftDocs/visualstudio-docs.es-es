---
title: "Iniciar el depurador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], iniciación del depurador"
  - "depurador [SDK de depuración], iniciar"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Iniciar el depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Iniciar el depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.  
  
## Secuencias de métodos y eventos  
  
1.  Eligiendo llama al \(SDM\) administrador de depuración de sesión mediante el menú de **Depurar** y, a continuación **Iniciar**.  Para obtener más información, consulte [Iniciar un programa](../../extensibility/debugger/launching-a-program.md).  
  
2.  El SDM llama al método de [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
3.  Basado en el modelo de \(DE\) proceso del motor de depuración, el método de `IDebugProgramNodeAttach2::OnAttach` devuelve uno de los métodos siguientes, que determina qué ocurre después.  
  
     Si se devuelve `S_FALSE` , el motor de depuración \(DE\) se debe cargar en partes de la máquina virtual.  
  
     O bien  
  
     Si se devuelve `S_OK` , el OF debe cargarse en partes de SDM.  El SDM realiza las tareas siguientes:  
  
    1.  Llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de.  
  
    2.  participa el OF.  
  
    3.  Llama a [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  El OF envía [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
5.  El OF envía [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
6.  El OF envía [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
7.  El OF envía [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
8.  El OF envía [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)