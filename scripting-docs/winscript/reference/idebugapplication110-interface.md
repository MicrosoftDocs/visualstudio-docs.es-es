---
title: "IDebugApplication110 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110 (Interfaz)"
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110 (Interfaz)
La interfaz de `IDebugApplication110` extiende la funcionalidad de [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md).  Puede obtener una instancia de esta interfaz llamando a QueryInterface en una implementación de [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IDebugApplication110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Realiza una llamada sincrónica en el subproceso principal.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Realiza una llamada asincrónica en el subproceso principal.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Esperas para que identificadores especificados cualquiera de los se van al permitir que las llamadas entre subprocesos se envían a este subproceso.  Este método se debe llamar al subproceso del depurador.|