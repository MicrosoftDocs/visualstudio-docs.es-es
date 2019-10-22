---
title: 'Idebugapplicationnodeevents (:: onRemoveChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574662"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Controla el evento cuando se quita un nodo secundario de un objeto de nodo de la aplicación de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prddpChild`  
 de Nodo de aplicación secundario que se ha quitado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento cuando se quita un nodo secundario de un objeto de nodo de la aplicación de depuración.  
  
 Los implementadores de la interfaz `IDebugApplicationNode` producen este evento.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplicationnodeevents (](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Idebugapplicationnodeevents (:: onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)    
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)