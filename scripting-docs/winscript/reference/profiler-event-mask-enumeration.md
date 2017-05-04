---
title: "PROFILER_EVENT_MASK (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PROFILER_EVENT_MASK (Enumeraci&#243;n)
Indica los tipos de eventos que se generan perfiles.  
  
## Sintaxis  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|PROFILER\_EVENT\_MASK\_TRACE\_SCRIPT\_FUNCTION\_CALL|Genera perfiles de las funciones que se definen en script usuario\- escrito y código dinámico.|  
|PROFILER\_EVENT\_MASK\_TRACE\_NATIVE\_FUNCTION\_CALL|Genera perfiles de las funciones nativas definidas por el motor de script.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL|Generación de perfiles todas las funciones definidas por el usuario y el script del motor, excepto llamadas en Document Object Model \(DOM\).|  
|PROFILER\_EVENT\_MASK\_TRACE\_DOM\_FUNCTION\_CALL|Genera perfiles de las funciones que llaman en DOM.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL\_WITH\_DOM|Generación de perfiles todas las funciones, como llamadas en DOM.|  
  
## Vea también  
 [Active Script Profiler \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)