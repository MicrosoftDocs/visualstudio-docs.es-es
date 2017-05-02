---
title: "IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:GetHostPid
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:GetHostPid"
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:GetHostPid
Devuelve el identificador de proceso de la aplicación host.  
  
## Sintaxis  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### Parámetros  
 `dwHostPid`  
 \[out\] identificador del proceso de host de El.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Utilizado por el IDE.  
  
## Vea también  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/es-es/2f65fa67-06b7-4053-8945-22383ab66343)