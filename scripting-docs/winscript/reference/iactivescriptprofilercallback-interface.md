---
title: IActiveScriptProfilerCallback (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0eb8ef209e1fc55fabf37c0c4469fd390f5a478
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146336"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback (Interfaz)
Proporciona métodos que se usan por el motor de scripting para notificar a un objeto de generador de perfiles cuando se producen eventos. Esta interfaz se implementa mediante el objeto de generador de perfiles.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Se llama para inicializar el objeto de generador de perfiles cuando se inicia la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Se llama para liberar y liberar el objeto de generador de perfiles, siempre que se detiene la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al analizador de objeto que el scripting del motor compila la secuencia de comandos.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al analizador de objeto que el scripting del motor encontró una función cuando se compila una secuencia de comandos.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica al objeto de generador de perfiles que el motor de scripting que se va a ejecutar una llamada de función que no es una llamada a Document Object Model (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al analizador de objeto que el motor de scripting termine de ejecutar una función llamada que no es una llamada en el DOM.|  
  
## <a name="remarks"></a>Comentarios  
 Notificación de llamadas de función en Document Object Model (DOM) proporcionada por el [IActiveScriptProfilerCallback2 (interfaz)](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Para agregar la capacidad de iniciar y detener la generación de perfiles cuando se ejecuta una secuencia de comandos, llame a los métodos siguientes. Mediante estos métodos, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar o detener la generación de perfiles.  
> 
> - Llame a [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
>   -   Llame a [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que pronto dejará de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)