---
title: "IMachineDebugManagerCookie (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie (interfaz)"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie (Interfaz)
Similar a la interfaz de `IMachineDebugManager` , la de la interfaz de `IMachineDebugManagerCookie` muestran las cookies.  
  
 Esta interfaz \(junto con la interfaz de `IDebugCookie` \) permite que los scripts se ejecutan en un proceso del depurador del archivo de comandos sin requerir que el depurador realiza el seguimiento de esos scripts.  
  
 Un depurador del archivo de comandos llama al método de `IDebugCookie::SetDebugCookie` en el administrador de proceso \(PDM\) de depuración.  A continuación, el PDM envía esta cookie junto con cualquier solicitud de agregar o quitar una aplicación de script en o desde el Administrador de depuración de equipos \(MDM\), utilizando los métodos de la interfaz de `IMachineDebugManagerCookie` .  El MDM continuación notifica a cada depurador de cambio, a excepción de que tiene ésta.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IMachineDebugManagerCookie` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Agrega una aplicación a la lista actual de la aplicación.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Devuelve un enumerador de lista actual de aplicaciones en ejecución.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Quita una aplicación de la lista actual de la aplicación.|  
  
## Vea también  
 [IMachineDebugManager \(Interfaz\)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie \(Interfaz\)](../../winscript/reference/idebugcookie-interface.md)