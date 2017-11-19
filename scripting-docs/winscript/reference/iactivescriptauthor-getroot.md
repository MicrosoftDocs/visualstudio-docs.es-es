---
title: IActiveScriptAuthor::GetRoot | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetRoot
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb20a896d54c2b8e85c93014e6bd8ad3c906f55c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Devuelve el `IScriptNode` raíz del árbol de secuencia de comandos del autor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppsp`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptNode` interfaz del nodo raíz.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)