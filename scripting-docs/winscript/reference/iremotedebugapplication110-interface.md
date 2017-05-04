---
title: "IRemoteDebugApplication110 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110 (Interfaz)"
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IRemoteDebugApplication110 (Interfaz)
Se utiliza para proporcionar las nuevas funciones que pueden llamar los depuradores del archivo de comandos y llamadores en proceso.  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IRemoteDebugApplication110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|Denominado para actualizar las opciones del depurador.  El valor predeterminado de las opciones a 0 \(SDO\_NONE\).|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|Devuelve el conjunto actual de las opciones se habilitados.|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|Devuelve el subproceso principal para los hosts que llaman SetSite.|