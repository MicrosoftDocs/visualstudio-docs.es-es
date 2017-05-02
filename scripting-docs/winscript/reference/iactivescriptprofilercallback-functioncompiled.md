---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
Notifica al objeto generador de perfiles que el motor de script encontró una función al compilar un script.  
  
## Sintaxis  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parámetros  
 `functionId`  
 \[in\] identificador único de la función.  Este id. es asignado por el motor de script.  
  
 `scriptId`  
 \[in\] identificador único del script que la función forma parte de.  
  
 `pwszFunctionName`  
 \[in\] nombre de la función, o null para una función anónima.  
  
 `pwszFunctionNameHint`  
 \[in\] deducía el nombre de la función, o null si el motor de script no infiere ningún nombre.  
  
 `pIDebugDocumentContext`  
 \[in\] si está disponible, el puntero a una interfaz de `IUnknown` que el generador de perfiles debe consultar un puntero de [IDebugDocumentContext \(Interfaz\)](../../winscript/reference/idebugdocumentcontext-interface.md) .  De lo contrario, es NULL.  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Comentarios  
 El motor de script puede proporcionar el contexto del documento sólo si es compatible con el host.  
  
## Vea también  
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)