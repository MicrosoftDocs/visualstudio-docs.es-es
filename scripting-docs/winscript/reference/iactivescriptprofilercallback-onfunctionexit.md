---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
Notifica al objeto generador de perfiles que el motor de script terminó de ejecutar una llamada de función que no es una llamada en Document Object Model \(DOM\).  
  
## Sintaxis  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### Parámetros  
 `scriptId`  
 \[in\] identificador único del script que la función forma parte de.  Este id. es asignado por el motor de script.  
  
 `functionId`  
 \[in\] identificador único de la función.  Este id. es asignado por el motor de script.  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Comentarios  
 Para las llamadas de DOM, el motor de script llama a [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) en lugar de `IActiveScriptProfilerCallback::OnFunctionExit`.  Esto es debido al elevado número de métodos y propiedades únicos en DOM.  
  
## Vea también  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)