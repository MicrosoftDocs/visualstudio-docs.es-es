---
title: IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf653e5623506a68e6353e3d9f97077592e87941
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091512"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica al analizador de objeto que el scripting del motor compila una secuencia de comandos. Este método se llama para todos los scripts que se compilan.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptId`  
 [in] El identificador único de la secuencia de comandos que se compiló. Este identificador es asignado por el motor de scripting.  
  
 `type`  
 [in] El tipo de la secuencia de comandos que se compiló. Los valores se definen en [PROFILER_SCRIPT_TYPE (enumeración)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Si está disponible, un puntero a un `IUnknown` interfaz que el generador de perfiles debe consultar un [IDebugDocumentContext (interfaz)](../../winscript/reference/idebugdocumentcontext-interface.md) puntero. En caso contrario, será null.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting puede proporcionar el contexto del documento solo si esto es compatible con el host.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)