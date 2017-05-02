---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
Recupera el estado actual del motor de script.  Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Sintaxis  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### Parámetros  
 `pss`  
 \[out\] la dirección de una variable que recibe un valor definido en la enumeración de [SCRIPTSTATE \(Enumeración\)](../../winscript/reference/scriptstate-enumeration.md) .  El valor indica el estado actual del motor de script asociado al subproceso de llamada.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_POINTER` si un puntero no válido se especificado.  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)