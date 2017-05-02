---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
Recupera el estado actual de un subproceso del script.  
  
## Sintaxis  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### Parámetros  
 `stidThread`  
 \[in\] identificador del subproceso que desean estados, o uno de los identificadores especiales siguientes de subprocesos:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTTHREADID\_BASE|El subproceso base; es decir, el subproceso en el que el motor de script se creó instancias.|  
|SCRIPTTHREADID\_CURRENT|El subproceso que se está ejecutando actualmente.|  
  
 `pstsState`  
 \[out\] dirección de una variable que recibe el estado del subproceso indicado.  Uno de los valores constantes con nombre indica el estado definidos por la enumeración de [SCRIPTTHREADSTATE \(Enumeración\)](../../winscript/reference/scriptthreadstate-enumeration.md) .  Si este parámetro no identifica el subproceso actual, el estado puede cambiar en cualquier momento.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
  
## Comentarios  
 Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)