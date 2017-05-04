---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
Obtiene el estado de este subproceso.  
  
## Sintaxis  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### Parámetros  
 `pState`  
 \[out\] la combinación de estado siguiente de subproceso marca:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|THREAD\_STATE\_RUNNING|0x00000001|Se está ejecutando el subproceso.|  
|THREAD\_STATE\_SUSPENDED|0x00000002|Subproceso suspendido.|  
|THREAD\_BLOCKED|0x00000004|Subproceso bloqueado.|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|El subproceso está fuera de contenido.|  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método obtiene el estado de este subproceso.  
  
## Vea también  
 [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)