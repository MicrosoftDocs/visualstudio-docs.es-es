---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
Inicio de generación de perfiles en el motor de script.  El motor de script crea una instancia del objeto de generador mediante una llamada a [CoCreateInstance](http://msdn.microsoft.com/es-es/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## Sintaxis  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### Parámetros  
 `clsidProfilerObject`  
 \[in\] identificador de clase \(CLSID\) del objeto generador de perfiles que se creará.  
  
 `dwEventMask`  
 \[in\] A una máscara de bits de 4 bytes que especifica los tipos de eventos.  Los bits se definen en [PROFILER\_EVENT\_MASK \(Enumeración\)](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 \[in\] Al valor de 4 bytes que se pasa al objeto generador de perfiles.  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|La generación de perfiles se habilita ya.|  
  
## Vea también  
 [IActiveScriptProfilerControl \(Interfaz\)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)