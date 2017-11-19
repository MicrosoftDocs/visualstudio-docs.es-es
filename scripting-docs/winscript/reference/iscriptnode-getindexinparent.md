---
title: IScriptNode::GetIndexInParent | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3862a48ff4649f018eec79bf0411f23bc9f6d7bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Devuelve el índice de un objeto de lista de nodos secundarios del elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pisn`  
 [out] Devuelve el índice de un objeto de lista de nodos secundarios del elemento primario.  
  
 Si este método es invocado por un `IScriptNode` del objeto que representa una página Web, este parámetro devuelve 0.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)