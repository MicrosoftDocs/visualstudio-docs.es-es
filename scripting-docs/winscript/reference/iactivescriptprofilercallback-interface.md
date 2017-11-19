---
title: IActiveScriptProfilerCallback (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback (Interfaz)
Proporciona métodos que se usan el motor de scripting para notificar a un objeto de generador de perfiles cuando se producen eventos. Esta interfaz está implementada por el objeto de generador de perfiles.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Se llama para inicializar el objeto de generador de perfiles cuando se inicie la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Se llama para liberar y liberar el objeto de generador de perfiles siempre que se detiene la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al generador de perfiles un objeto que el scripting del motor compilado de la secuencia de comandos.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al analizador de objeto que el scripting del motor encontró una función cuando se compila una secuencia de comandos.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica al objeto de generador de perfiles que el motor de scripting se va a ejecutar una llamada de función que no es una llamada en el modelo de objetos de documento (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al analizador de objeto que el motor de scripting terminado de ejecutar una función llamada que no es una llamada en el DOM.|  
  
## <a name="remarks"></a>Comentarios  
 Notificación de llamadas de función en el modelo de objetos de documento (DOM) proporcionada por el [IActiveScriptProfilerCallback2 (interfaz)](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Para agregar la capacidad de iniciar y detener la generación de perfiles cuando se ejecuta una secuencia de comandos, llame a los métodos siguientes. Mediante estos métodos, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar o detener la generación de perfiles.  
>   
>  -   Llame a [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
> -   Llame a [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que pronto dejará de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)