---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
Recupera información sobre un error que se produjo mientras el motor de script ejecuta un script.  
  
## Sintaxis  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### Parámetros  
 `pexcepinfo`  
 \[out\] dirección de una estructura de `EXCEPINFO` que recibe información de error.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL` si se ha producido un error.  
  
## Vea también  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)