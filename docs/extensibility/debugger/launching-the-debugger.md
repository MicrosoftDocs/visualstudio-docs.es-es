---
title: Iniciar el depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108935"
---
# <a name="launching-the-debugger"></a>Iniciar el depurador
Iniciar al depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.  
  
## <a name="sequences-of-methods-and-events"></a>Secuencias de métodos y eventos  
  
1.  El Administrador de sesión de depuración (SDM) se denomina eligiendo la **depurar** menú y, a continuación, elegir **iniciar**. Vea [ejecutar un programa](../../extensibility/debugger/launching-a-program.md) para obtener más información.  
  
2.  Las llamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
3.  Según el modelo de proceso del motor DE depuración, el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los métodos siguientes, que determina qué ocurre después.  
  
     Si `S_FALSE` se devuelve, el motor de depuración (Alemania) es que se va a cargar en el proceso de la máquina virtual.  
  
     -o bien-  
  
     Si `S_OK` se devuelve, es la DE que se va a cargar en el proceso de la SDM. El SDM, a continuación, realiza las tareas siguientes:  
  
    1.  Llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información de motor de la DE.  
  
    2.  Participa en la DE la creación.  
  
    3.  Llamadas [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Los envíos DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para el SDM con un `EVENT_SYNC` atributo.  
  
5.  Los envíos DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para el SDM con un `EVENT_SYNC` atributo.  
  
6.  Los envíos DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para el SDM con un `EVENT_SYNC` atributo.  
  
7.  Los envíos DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para el SDM con un `EVENT_SYNC` atributo.  
  
8.  Los envíos DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para el SDM con un `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Vea también  
 [Eventos del depurador que realiza la llamada](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicio de un programa](../../extensibility/debugger/launching-a-program.md)