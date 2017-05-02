---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
Notifica al objeto generador de perfiles que el motor de script está a punto de ejecutar una llamada de función que no sea una llamada en Document Object Model \(DOM\).  
  
## Sintaxis  
  
```  
HRESULT OnFunctionEnter(  
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
 Para las llamadas de DOM, el motor de script llama a [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) en lugar de `IActiveScriptProfilerCallback::OnFunctionEnter`.  Esto es debido al elevado número de métodos y propiedades únicos en DOM.  
  
## Vea también  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)