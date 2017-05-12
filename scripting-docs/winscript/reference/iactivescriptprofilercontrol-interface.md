---
title: "IActiveScriptProfilerControl (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerControl (Interfaz)
Implementado por el motor de script que permite generar perfiles.  Normalmente, un objeto que implementa `IActiveScriptProfilerControl` también implementa la interfaz de [IActiveScript](../../winscript/reference/iactivescript.md) .  En este caso, puede obtener un identificador de la interfaz de `IActiveScriptProfilerControl` llamando al método de `IUnknown::QueryInterface` en el objeto.  La interfaz proporciona los métodos necesarios para detener e iniciar la generación de perfiles en el motor de script.  
  
## Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Inicio de generación de perfiles en el motor de script.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Establece la máscara de evento del generador de perfiles en el motor de script.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Detener la generación de perfiles en el motor de script.|  
  
## Vea también  
 [Active Script Profiler \(Interfaces\)](../../winscript/reference/active-script-profiler-interfaces.md)