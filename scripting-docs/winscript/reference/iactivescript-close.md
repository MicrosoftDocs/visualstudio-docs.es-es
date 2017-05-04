---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
Hace que el motor de script para abandonar cualquier script actualmente cargado, para perder su estado, y liberar los punteros de interfaz que tenga que otros objetos, lo escribiendo en un estado cerrado.  Completan receptores de eventos, el texto se ejecutan del script, e invocaciones de macro que ya están en curso antes de los cambios de estado \(uso [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) de cancelar un subproceso en ejecución del script\).  Deben llamar a este método crear hospedado antes de que se libere para evitar problemas de referencia circular.  
  
## Sintaxis  
  
```  
HRESULT Close(void);  
```  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|`S_OK`|Correcto.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script ya estaba en estado cerrado\).|  
|`OLESCRIPT_S_PENDING`|El método se pusieron en cola correctamente, pero el estado no ha cambiado todavía.  Cuando los cambios de estado, el sitio deben llamar al método de [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|El método correcto, pero el script se ha cerrado ya.|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)