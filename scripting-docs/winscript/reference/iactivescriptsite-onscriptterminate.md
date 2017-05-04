---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
Informa al host que el script ha completado la ejecución.  
  
## Sintaxis  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### Parámetros  
 `pvarResult`  
 \[in\] dirección de una variable que contiene el resultado del script, o `NULL` si el script no genera ningún resultado.  
  
 `pexcepinfo`  
 \[in\] la dirección de una estructura de `EXCEPINFO` que contiene la información de excepción generó cuando el script finaliza, o `NULL` si no se genera ninguna excepción.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto.  
  
## Comentarios  
 El motor de script llama a este método antes de la llamada al método de [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , con el conjunto marca SCRIPTSTATE\_INITIALIZED, se complete.  Este método se puede utilizar para devolver el estado y resultados de finalización al host.  Observe que muchos lenguajes de scripting, basados en eventos de contraer host, tienen vidas que son definidas por el host.  En este caso, este método nunca puede llamar.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)