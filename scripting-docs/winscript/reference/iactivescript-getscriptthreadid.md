---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
Recupera un identificador script\-motor\- definido para el subproceso asociado al subproceso determinado de Win32.  
  
## Sintaxis  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### Parámetros  
 `dwWin32ThreadID` ,  
 \[in\] identificador del subproceso de un subproceso en ejecución de Win32 en el proceso actual.  Utilice la función de [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) para recuperar el identificador de subproceso del subproceso que se está ejecutando actualmente.  
  
 `pstidThread` ,  
 \[out\] dirección de una variable que recibe el identificador de subproceso de script asociado al subproceso determinado de Win32.  La interpretación de este identificador se permite al motor de script, pero puede ser simplemente una copia del identificador de subproceso de Windows.  Tenga en cuenta que si el subproceso de Win32 termina, este identificador no esté asignado y puede asignarse posteriormente a otro subproceso.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\) y por tanto no se errónea.|  
  
## Comentarios  
 El identificador recuperado se puede utilizar en llamadas posteriores a los métodos de control de la ejecución de subprocesos de scripting como el método de [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)