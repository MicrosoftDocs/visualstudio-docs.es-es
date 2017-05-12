---
title: "IRemoteDebugApplicationThread::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Resume"
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Resume
Reanudar el subproceso.  
  
## Sintaxis  
  
```  
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### Parámetros  
 `pdwCount`  
 \[out\] valor de suspensión para obtener el subproceso.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Cuando este método reanudar el subproceso, disminuye el recuento de suspensión.  
  
## Vea también  
 [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)