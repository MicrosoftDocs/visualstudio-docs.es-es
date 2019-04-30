---
title: IDebugApplicationThreadEvents110 (interfaz) | Documentos de Microsoft
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
ms.openlocfilehash: b2cdde46484f95aa57404ebe6b6cb4c86ef458c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440500"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 (Interfaz)
Agrega más eventos de subproceso. Estos eventos solo son locales. Es decir, puede suscribirse a ellas solo en el proceso que se está depurando, mediante el [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) aconsejar y desaconsejar métodos en objetos de subproceso de aplicación de PDM (los objetos que implementan [IDebugApplicationThread Interfaz](../../winscript/reference/idebugapplicationthread-interface.md)). Que se producen en el subproceso que se originan en.  
  
> [!IMPORTANT]
> Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IDebugActivationThreadEvents110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una llamada en el subproceso con el subproceso de PDM cambio ha comenzado.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|El subproceso está reanudando después de un punto de interrupción y estará activo una vez más.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|El subproceso se está suspendiendo un punto de interrupción y puede controlar las llamadas que requieren el subproceso se suspenda totalmente.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una llamada en el subproceso con el subproceso de PDM ha completado el cambio.|