---
title: 'Iactivescriptprofilercallback (:: OnFunctionEnter | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571687"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifica al objeto de generador de perfiles que el motor de scripting está a punto de ejecutar una llamada de función que no es una llamada al Document Object Model (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptId`  
 de IDENTIFICADOR único del script del que forma parte la función. El motor de scripting asigna este identificador.  
  
 `functionId`  
 de IDENTIFICADOR único de la función. El motor de scripting asigna este identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 El motor de scripting omite el valor devuelto de este método.  
  
## <a name="remarks"></a>Comentarios  
 En el caso de las llamadas DOM, el motor de scripting llama a [iactivescriptprofilercallback2 (:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) en lugar de `IActiveScriptProfilerCallback::OnFunctionEnter`. Esto se debe a un gran número de propiedades y métodos únicos en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [Iactivescriptprofilercallback (:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)    
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)