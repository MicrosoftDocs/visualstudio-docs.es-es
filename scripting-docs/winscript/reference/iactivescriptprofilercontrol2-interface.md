---
title: "IActiveScriptProfilerControl2 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2 (interfaz)"
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2 (Interfaz)
Proporciona métodos que agregan la capacidad de iniciar o de detener la generación de perfiles de cuando un script ejecuta.  
  
## Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores aplicables de script.  Esto permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al generador de perfiles que va a detener la generación de perfiles en todos los motores aplicables de script.  Esto permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] está ejecutando cuando se deja de generar perfiles.|  
  
## Vea también  
 [IActiveScriptProfilerControl \(Interfaz\)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Active Script Profiler \(Interfaces\)](../../winscript/reference/active-script-profiler-interfaces.md)