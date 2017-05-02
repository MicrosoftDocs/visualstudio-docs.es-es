---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
Coloca el motor de script en el estado con.  Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Sintaxis  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### Parámetros  
 `ss`  
 \[in\] establece el motor de script al estado determinada.  Puede ser uno de los valores definidos en la enumeración de [SCRIPTSTATE \(Enumeración\)](../../winscript/reference/scriptstate-enumeration.md) .  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|El motor de script no admite la transición al estado inicializado.  El host debe descartar este motor de scripting y crear, inicializar, y cargar un nuevo motor de script para lograr el mismo efecto.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\) y por tanto no se errónea.|  
|`OLESCRIPT_S_PENDING`|El método se pusieron en cola correctamente, pero el estado no ha cambiado todavía.  Cuando los cambios de estado, el sitio se llamará posteriores con el método de [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|El método correcto, pero el script ya estaba en el estado con.|  
  
## Comentarios  
 Para obtener más información sobre estados del motor de scripts, vea los estados del motor de script la sección de [Motores Windows Script](../../winscript/windows-script-engines.md) .  
  
## Vea también  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)