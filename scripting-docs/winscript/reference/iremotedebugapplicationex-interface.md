---
title: IRemoteDebugApplicationEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144412"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx (Interfaz)
Representa una aplicación en ejecución. No debe corresponder a un proceso del sistema operativo. Normalmente, un depurador tiene como destino una aplicación para la depuración. Normalmente, el Administrador de procesos de depuración implementa el objeto de aplicación.  
  
 Además de los métodos heredados de `IUnknown`, el `IRemoteDebugApplicationEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Devuelve el identificador de proceso para la aplicación host.|  
|GetHostMachineName|Devuelve el nombre del equipo que se ejecuta la aplicación host.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Establece el idioma para la localización del depurador.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Fuerza al depurador en modo paso a paso.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca un comando de interrupción.|  
|SetProxyBlanketAndAddRef|Actualiza la información de seguridad de COM en un servidor proxy para un objeto de depurador para garantizar la compatibilidad con la depuración remota de sistemas operativos basados en Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef versiones desde SetProxyBlanketAndAddRef.|