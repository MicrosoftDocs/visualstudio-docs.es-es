---
title: "IActiveScriptProfilerCallback2 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2 (interfaz)"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback2 (Interfaz)
Proporciona métodos que utiliza el motor de script para notificar a un objeto generador de perfiles cuando los eventos de documento \(DOM \(DOM\) aparecen.  Esta interfaz se implementa mediante el objeto generador de perfiles.  
  
## Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica al objeto generador de perfiles que el motor de script es capaz de ejecutar una llamada de función DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica al objeto generador de perfiles que el motor de script terminó de ejecutar una llamada de función DOM.|  
  
## Comentarios  
 La interfaz de `IActiveScriptProfilerCallback2` primero publicó con Internet Explorer 9.  
  
 Notificación de las llamadas de función que no son llamadas en DOM proporciona [IActiveScriptProfilerCallback \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Para agregar la capacidad de iniciar y detener la generación de perfiles de cuando un script ejecuta, llame a los métodos siguientes.  Mediante estos métodos, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar o detener la generación de perfiles.  
>   
>  -   Llame a [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
> -   Llame a [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que se pronto detendrá la generación de perfiles.  
  
## Vea también  
 [Active Script Profiler \(Interfaces\)](../../winscript/reference/active-script-profiler-interfaces.md)