---
title: "IDebugApplicationThread110 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110 (Interfaz)"
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThread110 (Interfaz)
Proporciona más funcionalidad para la interfaz de [IDebugApplicationThread \(Interfaz\)](../../winscript/reference/idebugapplicationthread-interface.md) .  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IDebugApplicationThread110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Realiza una llamada asincrónica en el subproceso principal.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Un recuento cuántos subprocesos de solicitudes de los mecanismos de conmutación de subproceso de PDM es actualmente procesamiento.  Normalmente 0 o 1, pero es posible para que sea más alto si el inicio de una llamada del subproceso que procesa pero desencadena un sincrónico indica en voz alta de subprocesos o suspende de otra forma el subproceso \(por ejemplo, desencadena un evento de IDebugApplicationEvents que se emite en el subproceso del depurador\)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) se ha asignado este subproceso y aún no ha finalizado.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Este subproceso está en un estado que procese las llamadas realizadas utilizando los mecanismos de conmutación de subproceso de PDM \(como SynchronousCallInThread\).|