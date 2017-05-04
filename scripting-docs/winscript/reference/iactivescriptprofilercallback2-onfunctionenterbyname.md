---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica al objeto generador de perfiles que el motor de script va a ejecutar una llamada de función Document Object Model \(DOM\).  
  
## Sintaxis  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### Parámetros  
 `pwszFunctionName`  
 \[in\] nombre de función que el motor de script va a ejecutar.  
  
 `scriptType`  
 \[in\] tipo de función.  Para las descripciones de valores válidos, vea [PROFILER\_SCRIPT\_TYPE \(Enumeración\)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Comentarios  
 Para las llamadas de DOM, el motor de script llama a este método en lugar de llamar a [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md).  Esto es debido al elevado número de métodos y propiedades únicos en DOM.  
  
## Vea también  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback2-interface.md)