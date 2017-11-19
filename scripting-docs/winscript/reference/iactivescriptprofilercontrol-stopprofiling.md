---
title: IActiveScriptProfilerControl::StopProfiling | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.StopProfiling
apilocation: scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63d837b0f7a59b1e3efc832c4d98cb7dcab5447c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Detiene la generación de perfiles en el motor de scripting. Este método llama a [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) en el objeto de generador de perfiles y, a continuación, lo libera.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hrShutdownReason`  
 [in] HRESULT que se va a pasar como un parámetro a la [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) método del objeto de generador de perfiles.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|No está habilitada la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)