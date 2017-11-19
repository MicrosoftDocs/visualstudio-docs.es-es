---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica al analizador de objeto que el scripting del motor terminado de ejecutar una llamada de función de Document Object Model (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pwszFunctionName`  
 [in] El nombre de la función que el motor de scripting terminado de ejecutarse.  
  
 `scriptType`  
 [in] El tipo de la función. Para obtener descripciones de los valores válidos, consulte [PROFILER_SCRIPT_TYPE (enumeración)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 Para las llamadas de DOM, el motor de scripting llama a este método en lugar de llamar [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Esto es debido al elevado número de únicos métodos y propiedades en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 (Interfaz)](../../winscript/reference/iactivescriptprofilercallback2-interface.md)