---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87f0b7e7a3cea4e3e59fb43ef9ddc2d4934552e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993350"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica al analizador de objeto que el scripting del motor de terminado de ejecutar una llamada de función de Document Object Model (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pwszFunctionName`  
 [in] El nombre de la función que el motor de scripting había terminado de ejecutarse.  
  
 `scriptType`  
 [in] El tipo de la función. Para obtener descripciones de los valores válidos, vea [PROFILER_SCRIPT_TYPE (enumeración)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 Para las llamadas de DOM, el motor de scripting, llama a este método en lugar de llamar [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Esto es debido al gran número de métodos únicos y propiedades en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 (Interfaz)](../../winscript/reference/iactivescriptprofilercallback2-interface.md)