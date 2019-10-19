---
title: 'Iscriptnode (:: GetParent | Microsoft Docs'
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
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572557"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Devuelve el objeto `IScriptNode` que es el elemento primario de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppsnParent`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz `IScriptNode` de la instancia primaria.  
  
 Si la clase implementa `IScriptEntry` o `IScriptScriptlet`, se devuelve un objeto `IScriptNode`.  
  
 Si la clase implementa `IScriptNode` (que representa una página web), se devuelve NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)