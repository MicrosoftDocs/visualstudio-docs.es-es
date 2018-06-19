---
title: IMachineDebugManagerCookie (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729625"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie (Interfaz)
Similar a la `IMachineDebugManager` interfaz, la `IMachineDebugManagerCookie` interfaz es compatible con las cookies de depuración.  
  
 Esta interfaz (junto con la `IDebugCookie` interfaz) permite que los scripts para que se ejecute en un proceso de depuración de secuencia de comandos sin necesidad de que el depurador realizar un seguimiento de los scripts.  
  
 Llama a un depurador de script el `IDebugCookie::SetDebugCookie` método en el Administrador de depurar de proceso (PDM). A continuación, el PDM envía esta cookie junto con cualquier solicitud para agregar o quitar una aplicación de script a o desde la máquina Debug Manager (MDM), utilizando los métodos de la `IMachineDebugManagerCookie` interfaz. MDM, a continuación, notifica a cada depurador del cambio, excepto aquel que tiene dicha cookie.  
  
 Además de los métodos heredados de `IUnknown`, el `IMachineDebugManagerCookie` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Agrega una aplicación en el que se ejecuta lista de aplicaciones.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Devuelve un enumerador de la lista actual de las aplicaciones en ejecución.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Quita una aplicación desde el que se ejecuta lista de aplicaciones.|  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManager (interfaz)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie (Interfaz)](../../winscript/reference/idebugcookie-interface.md)