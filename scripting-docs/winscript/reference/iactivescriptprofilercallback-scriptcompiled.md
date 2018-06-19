---
title: IActiveScriptProfilerCallback::ScriptCompiled | Documentos de Microsoft
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
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724705"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica al generador de perfiles un objeto que el scripting del motor compilado una secuencia de comandos. Se llama a este método para cada secuencia de comandos que se compila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptId`  
 [in] El identificador único de la secuencia de comandos que se compiló. Este identificador está asignado por el motor de scripting.  
  
 `type`  
 [in] El tipo de la secuencia de comandos que se compiló. Los valores se definen en [PROFILER_SCRIPT_TYPE (enumeración)](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Si está disponible, un puntero a un `IUnknown` interfaz que el generador de perfiles debe consultar un [IDebugDocumentContext (interfaz)](../../winscript/reference/idebugdocumentcontext-interface.md) puntero. En caso contrario, éste será null.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting puede proporcionar el contexto del documento sólo si esto es compatible con el host.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)