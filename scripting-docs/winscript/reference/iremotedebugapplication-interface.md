---
title: IRemoteDebugApplication (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication (Interfaz)
Representa una aplicación en ejecución. No es necesario que corresponda a un proceso de sistema operativo. Normalmente, un depurador tiene como destino una aplicación para la depuración. Normalmente, el Administrador de procesos de depuración implementa el objeto de aplicación.  
  
 Además de los métodos heredados de `IUnknown`, el `IRemoteDebugApplication` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continúa una aplicación que está actualmente en un punto de interrupción.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Hace que la aplicación puede interrumpir el depurador lo antes posible.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Se conecta a un depurador a esta aplicación.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Desconecta al depurador actual de la aplicación.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Devuelve el depurador actual conectado a la aplicación.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Proporciona un mecanismo para que el depurador IDE, ejecutar fuera de proceso a la aplicación, para crear objetos en el proceso de aplicación.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica si la aplicación está respondiendo.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera todos los subprocesos que se sabe que están asociados con la aplicación.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Devuelve el nombre de este nodo de la aplicación.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Devuelve el nodo de la aplicación en la que se agregan todos los nodos asociados a la aplicación.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera los contextos de expresión global para todos los lenguajes que se ejecutan en esta aplicación.|