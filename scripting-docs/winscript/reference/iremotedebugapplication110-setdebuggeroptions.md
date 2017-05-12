---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
Denominado para actualizar las opciones del depurador.  Este método se debe llamar a después de [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md).  El método de [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) automáticamente restablece en las opciones predeterminadas.  El valor predeterminado de las opciones a 0 \(SDO\_NONE\).  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### Parámetros  
 `mask`  
 La máscara de [SCRIPT\_DEBUGGER\_OPTIONS \(Enumeración\)](../../winscript/reference/script-debugger-options-enumeration.md) .  
  
 `value`  
 Valor del parámetro [SCRIPT\_DEBUGGER\_OPTIONS \(Enumeración\)](../../winscript/reference/script-debugger-options-enumeration.md).  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 \(Interfaz\)](../../winscript/reference/iremotedebugapplication110-interface.md)