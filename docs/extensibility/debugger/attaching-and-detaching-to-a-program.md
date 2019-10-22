---
title: Asociación y desasociación a un programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edbabb078bc46c55431276e9c1fe8d1f807d76f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350912"
---
# <a name="attaching-and-detaching-to-a-program"></a>Asociación y desasociación a un programa
Asociar al depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.

## <a name="sequence-of-methods-and-events"></a>Secuencia de métodos y eventos

1. El Administrador de depuración de la sesión (SDM) llama a la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.

    Según el modelo de proceso del motor DE depuración, el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los métodos siguientes, que determina lo que sucede a continuación.

    Si `S_FALSE` se devuelve, el motor de depuración se haya asociado correctamente al programa. En caso contrario, el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método se llama para completar el proceso de conexión.

    Si `S_OK` se devuelve es la DE que se cargue en el mismo proceso que el SDM. El SDM realiza las siguientes tareas:

   1. Las llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de la DE.

   2. Crea conjuntamente la DE.

   3. Las llamadas [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Los envíos DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.

3. Los envíos DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.

4. Los envíos DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) en el SDM con un `EVENT_SYNC_STOP` atributo.

   Cuando se desasocia un programa es un sencillo proceso de dos pasos, como se indica a continuación:

5. Las llamadas SDM [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Los envíos DE un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Vea también
- [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)