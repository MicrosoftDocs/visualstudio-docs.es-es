---
title: IScriptEntry::SetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ebccb57885480d34d79cbd27e99dc6a35b343d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144815"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Establece el texto que se encuentra en el cuerpo de un `IScriptEntry` bloque de script o un `IScriptScriptlet` scriptlet.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 [in] Para un `IScriptEntry` bloque de script, `psz` es el texto encerrado entre las etiquetas de script.  
  
 Para un `IScriptEntry` bloque de función, `psz` es el cuerpo de función.  
  
 Para un `IScriptScriptlet` objeto (que se deriva de `IScriptEntry`), `psz` es el texto del script del scriptlet.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (interfaz)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)