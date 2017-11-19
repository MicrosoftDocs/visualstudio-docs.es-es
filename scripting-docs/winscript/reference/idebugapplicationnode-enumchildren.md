---
title: IDebugApplicationNode::EnumChildren | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ab13f3a284b1b36550367e68ca5fe600db3be6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
Enumera los nodos secundarios de este nodo de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pperddp`  
 [out] La enumeración de los nodos secundarios de este nodo.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método enumera los nodos secundarios de este nodo de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)