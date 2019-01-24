---
title: IDebugApplicationThread110 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 170b345bdb4587d1fd29c1f0f906df0157abd877
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348924"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 (Interfaz)
Proporciona más funcionalidad para la [IDebugApplicationThread (interfaz)](../../winscript/reference/idebugapplicationthread-interface.md) interfaz.  
  
> [!IMPORTANT]
>  Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IDebugApplicationThread110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|Realiza una llamada asincrónica en el subproceso principal.|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|Recuento de cuántas solicitudes de subproceso del subproceso de PDM mecanismos de conmutación se están procesando actualmente. Normalmente, 0 o 1, pero 's posible que sea mayor, si una llamada de subproceso inicia el procesamiento pero desencadena una llamada sincrónica fuera del subproceso o de lo contrario suspende el subproceso (por ejemplo, al desencadenar un evento IDebugApplicationEvents que se emite en el depurador subproceso)|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) se ha llamado en este subproceso y no se ha completado.|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|Este subproceso está en un estado que puede procesar las llamadas realizadas mediante el subproceso de PDM conmutación mecanismos (por ejemplo, SynchronousCallInThread).|