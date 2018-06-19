---
title: IDebugApplicationThreadEvents110 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726275"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (Interfaz)
Agrega más eventos de subproceso. Estos eventos solo son locales. Es decir, puede suscribirse a ellos únicamente en el proceso que se está depurando, usando la [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) aconsejar y desaconsejar métodos en objetos de subproceso de aplicación de PDM (objetos que implementan [IDebugApplicationThread Interfaz](../../winscript/reference/idebugapplicationthread-interface.md)). Se producen en el subproceso que proceden del.  
  
> [!IMPORTANT]
>  Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IDebugActivationThreadEvents110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una llamada en el subproceso con el subproceso de PDM ha comenzado el cambio.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|El subproceso está reanudando después de un punto de interrupción y se activará una vez más.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|El subproceso se está suspendiendo para un punto de interrupción y puede controlar las llamadas que requieren el subproceso que se suspenda totalmente.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una llamada en el subproceso con el subproceso de PDM ha completado el cambio.|