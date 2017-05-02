---
title: "IRemoteDebugApplication110::GetMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetMainThread"
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IRemoteDebugApplication110::GetMainThread
Devuelve el subproceso principal para los hosts de nomenclatura [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), si no devuelve E\_FAIL.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
  
```  
  
#### Parámetros  
 `ppThread`  
 \[out\] main [IRemoteDebugApplicationThread \(Interfaz\)](../../winscript/reference/iremotedebugapplicationthread-interface.md)de El.  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 \(Interfaz\)](../../winscript/reference/iremotedebugapplication110-interface.md)