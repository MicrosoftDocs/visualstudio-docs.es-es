---
title: IScriptNode::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c990b5ba5c3d03d319e0eeced282c92cfbb5281
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151016"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Devuelve el `IScriptNode` objeto que es el elemento primario de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppsnParent`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptNode` interfaz de la instancia principal.  
  
 Si la clase implementa `IScriptEntry` o `IScriptScriptlet`, un `IScriptNode` se devuelve el objeto.  
  
 Si la clase implementa `IScriptNode` (que representa una página Web), se devuelve NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)