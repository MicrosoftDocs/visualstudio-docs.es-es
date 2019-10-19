---
title: Interfaz Iactivescriptprofilercontrol (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571601"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl (Interfaz)
Implementado por el motor de scripting que admite la generación de perfiles. Normalmente, un objeto que implementa la `IActiveScriptProfilerControl` también implementa la interfaz [IActiveScript](../../winscript/reference/iactivescript.md) . En este caso, puede obtener un identificador para la interfaz de `IActiveScriptProfilerControl` llamando al método `IUnknown::QueryInterface` en el objeto. La interfaz proporciona los métodos necesarios para detener e iniciar la generación de perfiles en el motor de scripting.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Inicia la generación de perfiles en el motor de scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Establece la máscara de eventos del generador de perfiles en el motor de scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Detiene la generación de perfiles en el motor de scripting.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)