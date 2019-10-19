---
title: 'Iactivescriptprofilercallback (:: Shutdown | Microsoft Docs'
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
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571645"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Se llama para informar al objeto del generador de perfiles cada vez que se detenga la generación de perfiles en un motor de scripting. De este modo, el objeto de generador de perfiles puede llamar a sus rutinas de limpieza, si es necesario. El motor de scripting también llama a este método cuando el motor de scripting se está cerrando o cuando se produce un error en una llamada a [iactivescriptprofilercallback (:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hrReason`  
 de Motivo del cierre. Si el motor de scripting se está cerrando, se pasa `S_OK`. Si la llamada a [iactivescriptprofilercallback (:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) devuelve un error HRESULT, se pasa HRESULT. De lo contrario, este valor se recupera de [iactivescriptprofilercontrol (:: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valor devuelto  
 El motor de scripting omite el valor devuelto de este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)