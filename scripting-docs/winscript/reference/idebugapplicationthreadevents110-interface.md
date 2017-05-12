---
title: "IDebugApplicationThreadEvents110 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThreadEvents110 (Interfaz)"
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplicationThreadEvents110 (Interfaz)
Agrega más eventos de subproceso.  Estos eventos son locales únicamente.  Es decir, puede suscribirse a ellos sólo en el proceso que se está depurando, utilizando [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) el muestran y los métodos de unadvise en la aplicación de PDM diferentes objetos \(los objetos que implementan [IDebugApplicationThread \(Interfaz\)](../../winscript/reference/idebugapplicationthread-interface.md)\).  Aparecen en el subproceso que proceden de.  
  
> [!IMPORTANT]
>  Esta interfaz se implementa por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Métodos  
 La interfaz `IDebugActivationThreadEvents110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una llamada en el subproceso utilizando conmutación de subproceso de PDM ha iniciado.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|El subproceso está reanudando de un punto de interrupción y se activa de nuevo.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|El subproceso está la suspensión de para un punto de interrupción y controlar las llamadas que requieren el subproceso ser suspendidas totalmente.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una llamada en el subproceso utilizando conmutación de subproceso de PDM ha finalizado.|