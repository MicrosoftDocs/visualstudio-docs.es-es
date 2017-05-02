---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
Notifica al objeto generador de perfiles que el motor de script compiló un script.  Se llama a este método para cada script se compile que.  
  
## Sintaxis  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parámetros  
 `scriptId`  
 \[in\] identificador único del script que se compiló.  Este id. es asignado por el motor de script.  
  
 `type`  
 \[in\] tipo del script que se compiló.  Los valores se definen en [PROFILER\_SCRIPT\_TYPE \(Enumeración\)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 \[in\] si está disponible, un puntero a una interfaz de `IUnknown` que el generador de perfiles debe consultar un puntero de [IDebugDocumentContext \(Interfaz\)](../../winscript/reference/idebugdocumentcontext-interface.md) .  Si no, esto será null.  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Comentarios  
 El motor de script puede proporcionar el contexto del documento sólo si es compatible con el host.  
  
## Vea también  
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)