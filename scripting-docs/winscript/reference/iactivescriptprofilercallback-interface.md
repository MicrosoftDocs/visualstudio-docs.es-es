---
title: "IActiveScriptProfilerCallback (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptProfilerCallback (Interfaz)
Proporciona métodos que utiliza el motor de script para notificar a un objeto generador de perfiles cuando se producen eventos.  Esta interfaz se implementa mediante el objeto generador de perfiles.  
  
## Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Denominado para inicializar el objeto de generador de perfiles siempre que genera un perfil se inicie en un motor de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Denominado para liberar y liberar el objeto generador de perfiles siempre que la generación de perfiles se detiene en un motor de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al objeto generador de perfiles que el motor de script compiló el script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al objeto generador de perfiles que el motor de script encontró una función al compilar un script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica al objeto generador de perfiles que el motor de script está a punto de ejecutar una llamada de función que no sea una llamada en Document Object Model \(DOM\).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al objeto generador de perfiles que el motor de script terminó de ejecutar una llamada de función que no es una llamada en DOM.|  
  
## Comentarios  
 Notificación de las llamadas de función de Document Object Model \(DOM\) proporcionan [IActiveScriptProfilerCallback2 \(Interfaz\)](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Para agregar la capacidad de iniciar y detener la generación de perfiles de cuando un script ejecuta, llame a los métodos siguientes.  Mediante estos métodos, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar o detener la generación de perfiles.  
>   
>  -   Llame a [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
> -   Llame a [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que se pronto detendrá la generación de perfiles.  
  
## Vea también  
 [Active Script Profiler \(Interfaces\)](../../winscript/reference/active-script-profiler-interfaces.md)