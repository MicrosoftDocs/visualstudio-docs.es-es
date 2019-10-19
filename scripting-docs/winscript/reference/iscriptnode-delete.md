---
title: Iscriptnode (::D iminar | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3522e5543d333443de5b1287c994bf29de51c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576301"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Elimina este árbol de objetos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parámetros  
 El método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Después de llamar al método `Delete`, el método [iscriptnode (:: Alive](../../winscript/reference/iscriptnode-alive.md) debe indicar que el nodo de script no está activo.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)