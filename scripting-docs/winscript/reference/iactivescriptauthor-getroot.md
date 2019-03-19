---
title: IActiveScriptAuthor::GetRoot | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetRoot
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6cdb3246ccae2eabb34696162f67e82a60374550
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146193"
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Devuelve el `IScriptNode` raíz del árbol de la secuencia de comandos del autor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppsp`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptNode` interfaz del nodo raíz.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)