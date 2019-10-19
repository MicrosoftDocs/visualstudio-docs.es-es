---
title: Interfaz Iactivescriptprofilercallback (| Microsoft Docs
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
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571717"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback (Interfaz)
Proporciona métodos que el motor de scripting utiliza para notificar a un objeto de generador de perfiles cuando se producen eventos. Esta interfaz se implementa mediante el objeto de generador de perfiles.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Se llama para inicializar el objeto de generador de perfiles cada vez que se inicia la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Se llama para liberar y liberar el objeto de generador de perfiles siempre que se detenga la generación de perfiles en un motor de scripting.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al objeto de generador de perfiles que el motor de scripting compiló el script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al objeto de generador de perfiles que el motor de scripting encontró una función al compilar un script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica al objeto de generador de perfiles que el motor de scripting está a punto de ejecutar una llamada de función que no es una llamada al Document Object Model (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al objeto de generador de perfiles que el motor de scripting ha finalizado la ejecución de una llamada de función que no es una llamada a DOM.|  
  
## <a name="remarks"></a>Comentarios  
 La [interfaz iactivescriptprofilercallback2 (](../../winscript/reference/iactivescriptprofilercallback2-interface.md)proporciona una notificación de llamadas a funciones en el Document Object Model (dom).  
  
> [!NOTE]
> Para agregar la capacidad de iniciar y detener la generación de perfiles cuando se ejecuta un script, llame a los métodos siguientes. Con estos métodos, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al iniciar o detener la generación de perfiles.  
> 
> - Llame a [iactivescriptprofilercontrol2 (:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
>   - Llame a [iactivescriptprofilercontrol2 (::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que detendrá pronto la generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)