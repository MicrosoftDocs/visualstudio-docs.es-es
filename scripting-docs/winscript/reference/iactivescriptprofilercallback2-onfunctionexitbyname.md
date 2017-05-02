---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica al objeto generador de perfiles que el motor de script terminó de ejecutar una llamada de función de Document Object Model \(DOM\).  
  
## Sintaxis  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### Parámetros  
 `pwszFunctionName`  
 \[in\] nombre de función que el motor de script terminó de ejecutarse.  
  
 `scriptType`  
 \[in\] tipo de función.  Para las descripciones de valores válidos, vea [PROFILER\_SCRIPT\_TYPE \(Enumeración\)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Comentarios  
 Para las llamadas de DOM, el motor de script llama a este método en lugar de llamar a [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md).  Esto es debido al elevado número de métodos y propiedades únicos en DOM.  
  
## Vea también  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback2-interface.md)