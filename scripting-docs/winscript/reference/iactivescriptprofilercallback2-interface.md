---
title: Interfaz Iactivescriptprofilercallback2 (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577298"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 (Interfaz)
Proporciona métodos que el motor de scripting utiliza para notificar a un objeto de generador de perfiles cuando se producen eventos de Document Object Model (DOM). Esta interfaz se implementa mediante el objeto de generador de perfiles.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica al objeto de generador de perfiles que el motor de scripting va a ejecutar una llamada de función DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica al objeto de generador de perfiles que el motor de scripting ha terminado de ejecutar una llamada de función DOM.|  
  
## <a name="remarks"></a>Comentarios  
 La interfaz de `IActiveScriptProfilerCallback2` se lanzó por primera vez con Internet Explorer 9.  
  
 La [interfaz iactivescriptprofilercallback (](../../winscript/reference/iactivescriptprofilercallback-interface.md)proporciona la notificación de llamadas de función que no son llamadas a Dom.  
  
> [!NOTE]
> Para agregar la capacidad de iniciar y detener la generación de perfiles cuando se ejecuta un script, llame a los métodos siguientes. Con estos métodos, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al iniciar o detener la generación de perfiles.  
> 
> - Llame a [iactivescriptprofilercontrol2 (:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar al generador de perfiles que ha iniciado la generación de perfiles.  
>   - Llame a [iactivescriptprofilercontrol2 (::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar al generador de perfiles que detendrá pronto la generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)