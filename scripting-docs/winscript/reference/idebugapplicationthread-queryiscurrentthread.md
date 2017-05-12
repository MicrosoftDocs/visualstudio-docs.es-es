---
title: "IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsCurrentThread"
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsCurrentThread
Determina si este subproceso es el subproceso que se está ejecutando actualmente.  
  
## Sintaxis  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y es el subproceso que se está ejecutando actualmente.|  
|`S_FALSE`|Éste no es el subproceso que se está ejecutando actualmente.|  
  
## Comentarios  
 Este método determina si este subproceso es el subproceso que se está ejecutando actualmente.  
  
## Vea también  
 [IDebugApplicationThread \(Interfaz\)](../../winscript/reference/idebugapplicationthread-interface.md)