---
title: Interfaz Idebugapplicationthreadevents110 (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984403"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (Interfaz)
Agrega más eventos de subproceso. Estos eventos solo son locales. Es decir, solo puede suscribirse a ellos en el proceso que se está depurando, mediante los métodos [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) Advise y unvise en objetos de subproceso de aplicación PDM (objetos que implementan la [interfaz idebugapplicationthread (](../../winscript/reference/idebugapplicationthread-interface.md)). Se producen en el subproceso del que proceden.  
  
> [!IMPORTANT]
> Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IDebugActivationThreadEvents110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Ha empezado una llamada al subproceso mediante el cambio de subprocesos de PDM.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|El subproceso se está reanudando desde un punto de interrupción y volverá a estar activo.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|El subproceso está suspendiendo un punto de interrupción y puede controlar llamadas que requieren que el subproceso se suspenda por completo.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Se ha completado una llamada al subproceso mediante el cambio de subprocesos de PDM.|