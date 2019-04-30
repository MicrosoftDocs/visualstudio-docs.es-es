---
title: IMachineDebugManagerCookie (interfaz) | Documentos de Microsoft
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
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977691"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie (Interfaz)
Similar a la `IMachineDebugManager` interfaz, el `IMachineDebugManagerCookie` interfaz admite cookies de depuración.  
  
 Esta interfaz (junto con el `IDebugCookie` interfaz) permitir secuencias de comandos ejecutar en un proceso de depuración de secuencias de comandos sin necesidad de que el depurador realizar un seguimiento de esas secuencias de comandos.  
  
 Llama un depurador de script el `IDebugCookie::SetDebugCookie` método en el proceso de depurar Manager (PDM). A continuación, el PDM envía esta cookie junto con cualquier solicitud para agregar o quitar una aplicación de script a o desde la máquina depurar Manager (MDM), mediante los métodos de la `IMachineDebugManagerCookie` interfaz. La MDM, a continuación, notifica a cada depurador del cambio, excepto aquel que tiene dicha cookie.  
  
 Además de los métodos heredados de `IUnknown`, el `IMachineDebugManagerCookie` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Agrega a la que se ejecuta una aplicación de lista de aplicaciones.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Devuelve un enumerador de la lista actual de aplicaciones en ejecución.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Quita el que se ejecuta en una aplicación lista de aplicaciones.|  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManager (interfaz)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie (Interfaz)](../../winscript/reference/idebugcookie-interface.md)