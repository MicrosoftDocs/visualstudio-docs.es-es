---
title: IActiveScriptProfilerControl2 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dad5d4a90eecdc6c93d86df9f9b18273bc471a4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349769"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 (Interfaz)
Proporciona métodos que agregan la capacidad de iniciar o detener la generación de perfiles cuando se ejecuta una secuencia de comandos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores de secuencias de comandos aplicables. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al generador de perfiles que se va a detener la generación de perfiles en todos los motores de secuencias de comandos aplicables. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando cuando se detiene la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)