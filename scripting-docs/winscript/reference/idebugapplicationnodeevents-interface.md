---
title: Interfaz Idebugapplicationnodeevents (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574714"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents (Interfaz)
Proporciona la interfaz de eventos para la interfaz `IDebugApplicationNode`.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz de `IDebugApplicationNodeEvents` expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Controla el evento cuando se agrega un nodo secundario a un objeto de nodo de la aplicación de depuración.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Controla el evento cuando se quita un nodo secundario de un objeto de nodo de la aplicación de depuración.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Controla un evento que indica que el objeto de nodo de la aplicación de depuración se desconectó de un nodo primario.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Controla un evento que indica que el objeto de nodo de la aplicación de depuración se ha asociado a un nodo primario.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationNode (Interfaz)](../../winscript/reference/idebugapplicationnode-interface.md)