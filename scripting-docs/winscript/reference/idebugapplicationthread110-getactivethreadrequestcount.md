---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
Devuelve el número de solicitudes de subproceso de los mecanismos de conmutación de subproceso de PDM que se están procesando actualmente.  Este número es normalmente 0 o 1.  Sin embargo, el número puede ser mayor si el inicio de una llamada del subproceso que procesa pero desencadena un sincrónico indica en voz alta de subproceso, o suspende de otra forma el subproceso y permite que las llamadas entrantes se procesan de nuevo \(por ejemplo, desencadena un evento de [IRemoteDebugApplicationEvents \(Interfaz\)](../../winscript/reference/iremotedebugapplicationevents-interface.md) , que se emite en el subproceso del depurador\).  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### Parámetros  
 `puiThreadRequests`  
 \[out\] número de solicitudes de subproceso.  
  
## Vea también  
 [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md)