---
title: IDebugApplicationNodeEvents::onAddChild | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df872cd14b6d7fcd455371d1601b2a4082fb39a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Controla el evento cuando se agrega un nodo secundario a un objeto de nodo de la aplicación de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prddpChild`  
 [in] El nodo de aplicación de depuración secundario que se agregó.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento cuando se agrega un nodo secundario a un objeto de nodo de la aplicación de depuración.  
  
 Los implementadores de la `IDebugApplicationNode` interfaz se genera este evento  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNodeEvents (interfaz)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)