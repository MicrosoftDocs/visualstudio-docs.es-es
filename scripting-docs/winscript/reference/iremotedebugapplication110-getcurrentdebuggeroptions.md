---
title: "IRemoteDebugApplication110::GetCurrentDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::GetCurrentDebuggerOptions"
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::GetCurrentDebuggerOptions
Devuelve el conjunto de opciones que se permiten actualmente.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### Parámetros  
 `pCurrentOptions`  
 \[out\] opciones de la actual de El.  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 \(Interfaz\)](../../winscript/reference/iremotedebugapplication110-interface.md)