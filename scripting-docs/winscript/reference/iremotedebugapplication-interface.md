---
title: "IRemoteDebugApplication (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication (interfaz)"
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication (Interfaz)
Representa una aplicación en ejecución.  No debe corresponder a un proceso del sistema operativo.  Normalmente, un depurador a una aplicación para la depuración.  El administrador de la depuración implementa normalmente el objeto application.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IRemoteDebugApplication` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continúa una aplicación que está actualmente en un punto de interrupción.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Hace que la aplicación para interrumpir el depurador en la primera oportunidad.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Se conecta a un depurador con esta aplicación.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Desconecta el depurador actual de la aplicación.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Devuelve el depurador actual conectado a la aplicación.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Proporciona un mecanismo para el depurador el IDE, hacia fuera\-de\- proceso actual con la aplicación, para crear objetos en el proceso de la aplicación.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica si la aplicación es sensible.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Muestra todos los subprocesos conocidos para asociar a la aplicación.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Devuelve el nombre de este nodo de la aplicación.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Devuelve el nodo de la aplicación en el que todos los nodos asociados a la aplicación se agregan.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera los contextos globales de expresiones para todos los lenguajes que se ejecutan en esta aplicación.|