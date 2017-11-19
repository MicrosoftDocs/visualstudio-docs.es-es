---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Notifica al objeto de generador de perfiles que el motor de scripting se va a ejecutar una llamada de función que no es una llamada en el modelo de objetos de documento (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptId`  
 [in] El identificador único de la secuencia de comandos que forma parte de la función. Este identificador está asignado por el motor de scripting.  
  
 `functionId`  
 [in] El identificador único de la función. Este identificador está asignado por el motor de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 Para las llamadas a DOM, se llama el motor de scripting [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) en lugar de `IActiveScriptProfilerCallback::OnFunctionEnter`. Esto es debido al elevado número de únicos métodos y propiedades en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)