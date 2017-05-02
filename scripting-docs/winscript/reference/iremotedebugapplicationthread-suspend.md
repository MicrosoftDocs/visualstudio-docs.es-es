---
title: "IRemoteDebugApplicationThread::Suspend | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Suspend
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Suspend"
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Suspend
Suspende el subproceso.  
  
## Sintaxis  
  
```  
HRESULT Suspend(  
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
 Cuando este método suspende el subproceso, aumenta el recuento de suspensión.  
  
## Vea también  
 [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)