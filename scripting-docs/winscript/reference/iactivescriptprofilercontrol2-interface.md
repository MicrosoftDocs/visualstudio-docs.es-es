---
title: Interfaz Iactivescriptprofilercontrol2 (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571531"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2 (Interfaz)
Proporciona métodos que agregan la capacidad de iniciar o detener la generación de perfiles cuando se ejecuta un script.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores de scripting aplicables. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al iniciar la generación de perfiles.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al generador de perfiles que va a detener la generación de perfiles en todos los motores de scripts aplicables. Esto le permite obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al detener la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptprofilercontrol (](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)