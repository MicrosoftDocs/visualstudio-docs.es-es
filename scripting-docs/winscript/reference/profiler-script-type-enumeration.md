---
title: "PROFILER_SCRIPT_TYPE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE (Enumeraci&#243;n)
Especifica el tipo de script.  
  
## Sintaxis  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|PROFILER\_SCRIPT\_TYPE\_USER|Especifica script usuario\- tipo.|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|Especifica la secuencia de comandos que se genera dinámicamente durante la ejecución.|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|Especifica el tipo de script para las funciones nativas y objetos definidos por el motor de script.|  
|PROFILER\_SCRIPT\_TYPE\_DOM|Especifica una llamada en Document Object Model \(DOM\) de Internet Explorer, por ejemplo, una llamada al método de `document.getElementById` .|  
  
## Vea también  
 [Active Script Profiler \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)