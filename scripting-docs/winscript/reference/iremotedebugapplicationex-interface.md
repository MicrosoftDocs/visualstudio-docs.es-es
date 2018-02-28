---
title: IRemoteDebugApplicationEx (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx (Interfaz)
Representa una aplicación en ejecución. No es necesario que corresponda a un proceso del sistema operativo. Normalmente, un depurador tiene como destino una aplicación para la depuración. Normalmente, el Administrador de procesos de depuración implementa el objeto de aplicación.  
  
 Además de los métodos heredados de `IUnknown`, el `IRemoteDebugApplicationEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Devuelve el identificador de proceso de la aplicación host.|  
|GetHostMachineName|Devuelve el nombre del equipo que se ejecuta la aplicación host.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Establece el idioma para la localización de depurador.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Fuerza al depurador en modo paso a paso.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca un comando de interrupción.|  
|SetProxyBlanketAndAddRef|Actualiza la información de seguridad de COM en un servidor proxy para un objeto de depurador para garantizar su compatibilidad con la depuración remota de sistemas operativos basados en Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef de versiones de SetProxyBlanketAndAddRef.|