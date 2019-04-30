---
title: IActiveScriptProfilerCallback::Shutdown | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 091ccc30f16081fdca8f10778efec208ef5ccb16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993428"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Se llama para informar al objeto de generador de perfiles, siempre que se detiene la generación de perfiles en un motor de scripting. De este modo, el objeto de generador de perfiles puede llamar a sus rutinas de limpieza, si es necesario. Este método también se llama por el motor de scripting cuando se está cerrando el motor de scripting, o cuando una llamada a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) se produce un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hrReason`  
 [in] El motivo del cierre. Si se está cerrando el motor de scripting, `S_OK` se pasa. Si la llamada a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) devuelve un valor HRESULT de error, se pasa el valor HRESULT. En caso contrario, este valor se recupera de [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)