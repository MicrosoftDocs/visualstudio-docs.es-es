---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724995"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permite a un host inteligente determinar cómo tratar los errores de tiempo de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 [in] El error de tiempo de ejecución que se ha producido  
  
 `pfEnterDebugger`  
 [out] Marca que indica si se debe pasar el error en el depurador al realizar la depuración JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Marca que indica si se debe llamar a `IActiveScriptSite::OnScriptError` cuando el usuario decide continuar sin depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Los valores posibles incluyen, pero no están limitados al valor en la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente puede utilizar este método para determinar cómo tratar los errores de tiempo de ejecución.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug (Interfaz)](../../winscript/reference/iactivescriptsitedebug-interface.md)