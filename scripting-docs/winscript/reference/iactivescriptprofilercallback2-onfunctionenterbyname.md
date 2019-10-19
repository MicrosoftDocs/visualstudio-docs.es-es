---
title: 'Iactivescriptprofilercallback2 (:: OnFunctionEnterByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571640"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica al objeto de generador de perfiles que el motor de scripting va a ejecutar una llamada de función Document Object Model (DOM).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pwszFunctionName`  
 de Nombre de la función que va a ejecutar el motor de scripting.  
  
 `scriptType`  
 de Tipo de la función. Para obtener descripciones de valores válidos, consulte [enumeración PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valor devuelto  
 El motor de scripting omite el valor devuelto de este método.  
  
## <a name="remarks"></a>Comentarios  
 En el caso de las llamadas DOM, el motor de scripting llama a este método en lugar de llamar a [iactivescriptprofilercallback (:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Esto se debe a un gran número de propiedades y métodos únicos en el DOM.  
  
## <a name="see-also"></a>Vea también  
 [Iactivescriptprofilercallback2 (:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)    
 [IActiveScriptProfilerCallback2 (Interfaz)](../../winscript/reference/iactivescriptprofilercallback2-interface.md)