---
title: "IRemoteDebugApplicationThread::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetDescription
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetDescription"
ms.assetid: 69842e9e-7c1c-4841-a6b2-31505fe85738
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetDescription
Obtiene la descripción y el estado de este subproceso.  
  
## Sintaxis  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription,  
   BSTR*  pbstrState  
);  
```  
  
#### Parámetros  
 `pbstrDescription`  
 \[out\] descripción de este subproceso.  
  
 `pbstrState`  
 \[out\] descripción del estado del subproceso.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método obtiene la descripción y el estado de este subproceso.  
  
## Vea también  
 [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)