---
title: 'Iscriptnode (:: GetCookie | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetCookie
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetCookie
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91428ca617c5c9e7b2bf88fc9c405f1d1610de1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572218"
---
# <a name="iscriptnodegetcookie"></a>IScriptNode::GetCookie
Devuelve un valor definido por la aplicación que se utiliza para asociar un Scriptlet con el objeto host.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwCookie`  
 enuncia Para un objeto `IScriptEntry`, devuelve el valor de cookie definido por la aplicación.  
  
 Para un `IScriptNode` objeto que representa una página web, devuelve 0.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)