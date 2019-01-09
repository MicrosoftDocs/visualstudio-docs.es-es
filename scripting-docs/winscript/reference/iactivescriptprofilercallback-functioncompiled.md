---
title: IActiveScriptProfilerCallback::FunctionCompiled | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4bd032914605c61b13a0a56a42e510c2af252f7e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091408"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica al analizador de objeto que el scripting del motor encontró una función cuando se compila una secuencia de comandos.  
  
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
 [in] El identificador único de la función. Este identificador es asignado por el motor de scripting.  
  
 `scriptId`  
 [in] El identificador único de la secuencia de comandos que forma parte de la función.  
  
 `pwszFunctionName`  
 [in] El nombre de la función, o null para una función anónima.  
  
 `pwszFunctionNameHint`  
 [in] Nombre de la función, o null si el motor de scripting no infiere cualquier nombre deducido.  
  
 `pIDebugDocumentContext`  
 [in] Si está disponible, el puntero a un `IUnknown` interfaz que el generador de perfiles debe consultar un [IDebugDocumentContext (interfaz)](../../winscript/reference/idebugdocumentcontext-interface.md) puntero. De lo contrario, es NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting puede proporcionar el contexto del documento solo si esto es compatible con el host.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)