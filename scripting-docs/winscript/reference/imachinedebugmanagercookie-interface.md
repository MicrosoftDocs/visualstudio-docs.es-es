---
title: Interfaz Imachinedebugmanagercookie (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573883"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie (Interfaz)
De forma similar a la interfaz de `IMachineDebugManager`, la interfaz de `IMachineDebugManagerCookie` admite cookies de depuración.  
  
 Esta interfaz (junto con la interfaz `IDebugCookie`) permite que los scripts se ejecuten en un proceso del depurador de scripts sin necesidad de que el depurador realice un seguimiento de esos scripts.  
  
 Un depurador de script llama al método `IDebugCookie::SetDebugCookie` en el administrador de depuración de proceso (PDM). A continuación, el PDM envía esta cookie junto con cualquier solicitud para agregar o quitar una aplicación de script a o desde el administrador de depuración de máquina (MDM), mediante los métodos de la interfaz de `IMachineDebugManagerCookie`. A continuación, MDM notifica cada depurador del cambio, excepto para el que tiene esa cookie.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz de `IMachineDebugManagerCookie` expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Agrega una aplicación a la lista de aplicaciones en ejecución.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Devuelve un enumerador de la lista actual de aplicaciones en ejecución.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Quita una aplicación de la lista de aplicaciones en ejecución.|  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz imachinedebugmanager (](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IDebugCookie (Interfaz)](../../winscript/reference/idebugcookie-interface.md)