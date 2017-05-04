---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
Informa al motor de script el sitio de la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) proporcionado por el host.  Llame a este método antes de que se utilice cualquier otro método de interfaz de [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## Sintaxis  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### Parámetros  
 `pScriptSite`  
 \[in\] dirección del sitio host\- proporcionado de script esté asociada a esta instancia del motor de script.  El sitio se debe asignar de forma exclusiva a esta instancia del motor de script; no se puede compartir con otros los motores de scripting.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|Un error sin especificar producido; el motor de script no pudo terminar de inicializar el sitio.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, un sitio se estableció ya\).|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)