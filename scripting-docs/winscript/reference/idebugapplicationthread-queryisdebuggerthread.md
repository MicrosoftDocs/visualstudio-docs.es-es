---
title: "IDebugApplicationThread::QueryIsDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.QueryIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::QueryIsDebuggerThread"
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::QueryIsDebuggerThread
Determina si este subproceso es el subproceso del depurador.  
  
## Sintaxis  
  
```  
HRESULT QueryIsDebuggerThread();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente y es el subproceso del depurador.|  
|`S_FALSE`|Éste no es el subproceso del depurador.|  
  
## Comentarios  
 Este método determina si este subproceso es el subproceso del depurador.  
  
## Vea también  
 [IDebugApplicationThread \(Interfaz\)](../../winscript/reference/idebugapplicationthread-interface.md)