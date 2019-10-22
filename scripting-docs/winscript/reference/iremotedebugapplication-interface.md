---
title: IRemoteDebugApplication (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944233"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication (Interfaz)
Representa una aplicación en ejecución. No debe corresponder a un proceso del sistema operativo. Normalmente, un depurador tiene como destino una aplicación para la depuración. Normalmente, el Administrador de procesos de depuración implementa el objeto de aplicación.  
  
 Además de los métodos heredados de `IUnknown`, el `IRemoteDebugApplication` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continúa una aplicación que está actualmente en un punto de interrupción.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Hace que la aplicación interrumpir el depurador lo antes posible.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Se conecta a un depurador a esta aplicación.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Desconecta al depurador actual de la aplicación.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Devuelve el depurador actual conectado a la aplicación.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Proporciona un mecanismo para el IDE, ejecución fuera de proceso a la aplicación, para crear objetos en el proceso de aplicación del depurador.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica si la aplicación es la capacidad de respuesta.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera todos los subprocesos que se sabe que están asociados con la aplicación.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Devuelve el nombre de este nodo de la aplicación.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Devuelve el nodo de la aplicación en la que se agregan todos los nodos asociados con la aplicación.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera los contextos de expresión global para todos los idiomas que se ejecutan en esta aplicación.|