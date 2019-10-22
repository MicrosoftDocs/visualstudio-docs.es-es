---
title: 'Iactivescriptprofilercallback (:: ScriptCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571664"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Notifica al objeto de generador de perfiles que el motor de scripting compiló un script. Se llama a este método para cada script que se compila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `scriptId`  
 de IDENTIFICADOR único del script que se compiló. El motor de scripting asigna este identificador.  
  
 `type`  
 de Tipo del script que se compiló. Los valores se definen en la [enumeración PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 de Si está disponible, un puntero a una interfaz `IUnknown` que el generador de perfiles debe consultar para un puntero de la [interfaz idebugdocumentcontext (](../../winscript/reference/idebugdocumentcontext-interface.md) . De lo contrario, será null.  
  
## <a name="return-value"></a>Valor devuelto  
 El motor de scripting omite el valor devuelto de este método.  
  
## <a name="remarks"></a>Comentarios  
 El motor de scripting puede proporcionar el contexto del documento solo si el host lo admite.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)