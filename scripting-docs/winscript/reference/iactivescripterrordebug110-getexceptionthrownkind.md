---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
Devuelve un valor que indica la clase de excepción producida.  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 \(Interfaz\)](../../winscript/reference/iactivescripterrordebug110-interface.md) se implementa mediante PDM versión 11.0 y versiones posteriores.  Se encuentra en activdbg100.h.  
  
## Sintaxis  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### Parámetros  
 `pExceptionKind`  
 \[out\] La clase de excepción que se produce \(por ejemplo, primera aparición o no controlada\), representada por un valor de la enumeración [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND \(Enumeración\)](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md).  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Vea también  
 [IActiveScriptErrorDebug110 \(Interfaz\)](../../winscript/reference/iactivescripterrordebug110-interface.md)