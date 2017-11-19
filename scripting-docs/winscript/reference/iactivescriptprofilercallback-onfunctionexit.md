---
title: IActiveScriptProfilerCallback::OnFunctionExit | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a3343c7e3747c48a4c43a1c1ac17fe6502aee3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
Notifica al analizador de objeto que el motor de scripting terminado de ejecutar una función llamada que no es una llamada en el modelo de objetos de documento (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnFunctionExit(  
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
 Para las llamadas a DOM, se llama el motor de scripting [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) en lugar de `IActiveScriptProfilerCallback::OnFunctionExit`. Esto es debido al elevado número de únicos métodos y propiedades en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)