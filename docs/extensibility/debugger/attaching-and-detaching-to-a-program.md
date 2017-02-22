---
title: "Asociar y desasociar un programa | Microsoft Docs"
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
  - "motores de depuración, asociar a programas"
  - "motores de depuración, cuando se desasocia de programas"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Asociar y desasociar un programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Asociar el depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.  
  
## Secuencia de métodos y eventos  
  
1.  El administrador de depuración de sesión \(SDM\) llama al método de [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
     Basado en el modelo de \(DE\) proceso del motor de depuración, el método de `IDebugProgramNodeAttach2::OnAttach` devuelve uno de los métodos siguientes, que determina qué ocurre después.  
  
     Si se devuelve `S_FALSE` , el motor de depuración se ha asociado correctamente al programa.  Si no, el método de [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) se denomina para completar el proceso de asociar.  
  
     Si se devuelve `S_OK` , el OF debe cargarse en el mismo proceso que el SDM.  El SDM realiza las tareas siguientes:  
  
    1.  Llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de.  
  
    2.  participa el OF.  
  
    3.  Llama a [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  El OF envía [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
3.  El OF envía [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM con un atributo de `EVENT_SYNC` .  
  
4.  El OF envía [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM con un atributo de `EVENT_SYNC_STOP` .  
  
 Cuando se desasocia un programa es un proceso sencillo, de dos fases, como sigue:  
  
1.  El SDM llama [Desasociar](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  El OF envía [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)