---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
Establece una máscara de bits de 4 bytes que especifique los tipos de eventos que el motor de script debe activar.  
  
## Sintaxis  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### Parámetros  
 `dwEventMask`  
 \[in\] A una máscara de bits de 4 bytes que especifica los tipos de eventos.  Los bits se definen en [PROFILER\_EVENT\_MASK \(Enumeración\)](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La generación de perfiles no está habilitada.|  
  
## Vea también  
 [IActiveScriptProfilerControl \(Interfaz\)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)