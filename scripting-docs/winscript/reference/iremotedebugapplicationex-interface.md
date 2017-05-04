---
title: "IRemoteDebugApplicationEx (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx (Interfaz)"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx (Interfaz)
Representa una aplicación en ejecución.  No debe corresponder a un proceso del sistema operativo.  Normalmente, un depurador a una aplicación para la depuración.  El administrador de la depuración implementa normalmente el objeto application.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IRemoteDebugApplicationEx` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Devuelve el identificador de proceso de la aplicación host.|  
|GetHostMachineName|Devuelve el nombre del equipo que la aplicación host se está ejecutando.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Establece el idioma de la localización del depurador.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Fuerza el depurador en modo paso a paso.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca un comando de interrupción.|  
|SetProxyBlanketAndAddRef|La información de seguridad COM de las actualizaciones de un proxy para que un objeto del depurador asegurarse compatibilidad con la depuración remota de Windows 95 en los sistemas operativos.|  
|ReleaseFromSetProxyBlanket|Versiones AddRef de SetProxyBlanketAndAddRef.|