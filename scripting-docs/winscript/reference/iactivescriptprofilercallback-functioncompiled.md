---
title: 'Iactivescriptprofilercallback (:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576478"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica al objeto de generador de perfiles que el motor de scripting encontró una función al compilar un script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `functionId`  
 de IDENTIFICADOR único de la función. El motor de scripting asigna este identificador.  
  
 `scriptId`  
 de IDENTIFICADOR único del script del que forma parte la función.  
  
 `pwszFunctionName`  
 de El nombre de la función o null para una función anónima.  
  
 `pwszFunctionNameHint`  
 de Nombre deducido de la función, o null si el motor de scripting no infiere ningún nombre.  
  
 `pIDebugDocumentContext`  
 de Si está disponible, el puntero a una interfaz `IUnknown` que el generador de perfiles debe consultar para un puntero de la [interfaz idebugdocumentcontext (](../../winscript/reference/idebugdocumentcontext-interface.md) . De lo contrario, es NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 El motor de scripting omite el valor devuelto de este método.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting puede proporcionar el contexto del documento solo si el host lo admite.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)