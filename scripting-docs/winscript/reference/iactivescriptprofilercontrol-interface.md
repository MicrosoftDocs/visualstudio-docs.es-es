---
title: IActiveScriptProfilerControl (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349496"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl (Interfaz)
Implementado por el motor de scripting que admite la generación de perfiles. Normalmente, un objeto que implementa el `IActiveScriptProfilerControl` también implementa el [IActiveScript](../../winscript/reference/iactivescript.md) interfaz. En este caso, puede obtener un identificador para el `IActiveScriptProfilerControl` interfaz mediante una llamada a la `IUnknown::QueryInterface` método en el objeto. La interfaz proporciona los métodos necesarios para detener e iniciar la generación de perfiles en el motor de scripting.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Inicia la generación de perfiles en el motor de scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Establece el generador de perfiles de máscara de eventos en el motor de scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Detiene la generación de perfiles en el motor de scripting.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler (Interfaces)](../../winscript/reference/active-script-profiler-interfaces.md)