---
title: "IDebugApplicationThread (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread (interfaz)"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread (Interfaz)
Permite que los motores y hosts de lenguaje proporcionan la sincronización de subprocesos y mantener información de estado subproceso\- específica de depuración.  Esta interfaz extiende la interfaz de `IRemoteDebugApplicationThread` para proporcionar acceso de no remoto al subproceso.  
  
 Además de los métodos heredados de `IRemoteDebugApplicationThread`, la interfaz `IDebugApplicationThread` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Proporciona un mecanismo para el llamador para ejecutar código en el subproceso de la aplicación.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina si este subproceso es el subproceso que se está ejecutando actualmente.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina si este subproceso es el subproceso del depurador.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Establece la descripción de este subproceso.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Establece la descripción del estado del subproceso.|