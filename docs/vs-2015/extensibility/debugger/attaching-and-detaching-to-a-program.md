---
title: Asociación y desasociación a un programa | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6915d54dca921f9600a51c3501ed9a4808bca199
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288709"
---
# <a name="attaching-and-detaching-to-a-program"></a>Asociación a un programa y desasociación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Asociar al depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.  
  
## <a name="sequence-of-methods-and-events"></a>Secuencia de métodos y eventos  
  
1.  El Administrador de depuración de la sesión (SDM) llama a la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
     Según el modelo de proceso del motor DE depuración, el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los métodos siguientes, que determina lo que sucede a continuación.  
  
     Si `S_FALSE` se devuelve, el motor de depuración se haya asociado correctamente al programa. En caso contrario, el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método se llama para completar el proceso de conexión.  
  
     Si `S_OK` se devuelve es la DE que se cargue en el mismo proceso que el SDM. El SDM realiza las siguientes tareas:  
  
    1.  Las llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de la DE.  
  
    2.  Crea conjuntamente la DE.  
  
    3.  Las llamadas [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Los envíos DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
3.  Los envíos DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
4.  Los envíos DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) en el SDM con un `EVENT_SYNC_STOP` atributo.  
  
 Cuando se desasocia un programa es un sencillo proceso de dos pasos, como se indica a continuación:  
  
1.  Las llamadas SDM [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Los envíos DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)

