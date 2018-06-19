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
ms.openlocfilehash: 9bc0dfa31b37a6bf99427c8eddfe2bd038da9b9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724755"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 (Interfaz)
Proporciona métodos que agregan la capacidad de iniciar o detener la generación de perfiles cuando se ejecuta una secuencia de comandos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al generador de perfiles que se ha iniciado en todos los motores de scripts aplicable de generación de perfiles. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al generador de perfiles que se van a detener la generación de perfiles en todos los motores de secuencias de comandos es aplicable. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta cuando se detiene la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)