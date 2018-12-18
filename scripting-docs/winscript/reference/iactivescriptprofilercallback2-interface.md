---
title: IActiveScriptProfilerCallback2 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6109e028dfc51a88314ce597a67847e95f7eaaed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815707"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 (Interfaz)
Proporciona métodos que se utilizan el motor de scripting para notificar a un objeto de generador de perfiles cuando se producen eventos de Document Object Model (DOM). Esta interfaz se implementa mediante el objeto de generador de perfiles.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica al objeto de generador de perfiles que el motor de scripting se va a ejecutar una llamada de función DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica al analizador de objeto que el scripting del motor de terminado de ejecutar una llamada de función DOM.|  
  
## <a name="remarks"></a>Comentarios  
 El `IActiveScriptProfilerCallback2` interfaz por primera vez con Internet Explorer 9.  
  
 Notificación de llamadas a funciones que no son llamadas en el DOM proporcionada por el [IActiveScriptProfilerCallback (interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Para agregar la capacidad de iniciar y detener la generación de perfiles cuando se ejecuta una secuencia de comandos, llame a los métodos siguientes. Mediante estos métodos, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar o detener la generación de perfiles.  
> 
> - Llame a [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
>   -   Llame a [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que pronto dejará de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)