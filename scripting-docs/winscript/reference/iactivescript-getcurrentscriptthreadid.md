---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
Recupera un identificador script\-motor\- definido para el subproceso que se está ejecutando actualmente.  El identificador se puede utilizar en llamadas subsiguientes a los métodos de la ejecución\- CONTROL de subprocesos de scripting como el método de [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## Sintaxis  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### Parámetros  
 `pstidThread`  
 \[out\] la dirección de una variable que recibe el identificador de subproceso de script asociado al subproceso actual.  La interpretación de este identificador se permite al motor de script, pero puede ser simplemente una copia del identificador de subproceso de Windows.  Si el subproceso de Win32 termina, este identificador no esté asignado y puede asignarse posteriormente a otro subproceso.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_POINTER` si un puntero no válido se especificado.  
  
## Comentarios  
 Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)