---
title: 'Idebugapplicationnode (:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574786"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Agrega este nodo de aplicación al árbol de proyecto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdanParent`  
 de Árbol del proyecto en el que se va a agregar este nodo de aplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método agrega este nodo de aplicación al árbol del proyecto, utilizando `pdanParent` como elemento primario. Si `pdanParent` es `NULL`, este nodo de aplicación será el nodo de nivel superior.  
  
## <a name="see-also"></a>Vea también  
 [Idebugapplicationnode (::D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)