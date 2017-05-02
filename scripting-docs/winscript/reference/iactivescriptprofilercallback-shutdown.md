---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
Denominado para informar al objeto generador de perfiles siempre que la generación de perfiles se detiene en un motor de script.  De esta manera, el objeto generador de perfiles puede llamar a rutinas de limpieza, si procede.  Este método también llama el motor de script cuando el motor de script está cerrándose, o cuando una llamada a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) .  
  
## Sintaxis  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### Parámetros  
 `hrReason`  
 \[in\] motivo del cierre.  Si el motor de script está cerrándose, se pasa `S_OK` .  Si la llamada a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) devuelve un error HRESULT, se pasa el HRESULT.  De lo contrario, este valor se recupera de [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## Valor devuelto  
 El valor devuelto de este método es omitido por el motor de script.  
  
## Vea también  
 [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md)