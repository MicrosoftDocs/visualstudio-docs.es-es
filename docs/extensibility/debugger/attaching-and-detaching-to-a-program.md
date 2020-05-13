---
title: Adjuntar y separar a un programa ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739269"
---
# <a name="attaching-and-detaching-to-a-program"></a>Adjuntar y separar a un programa
La asociación del depurador requiere el envío de la secuencia correcta de métodos y eventos con los atributos adecuados.

## <a name="sequence-of-methods-and-events"></a>Secuencia de métodos y eventos

1. El administrador de depuración de sesión (SDM) llama al método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    En función del modelo de proceso `IDebugProgramNodeAttach2::OnAttach` del motor de depuración (DE), el método devuelve uno de los métodos siguientes, que determina lo que sucede a continuación.

    Si `S_FALSE` se devuelve, el motor de depuración se ha asociado correctamente al programa. De lo contrario, se llama al método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) para completar el proceso de conexión.

    Si `S_OK` se devuelve, el DE se cargará en el mismo proceso que el SDM. El SDM realiza las siguientes tareas:

   1. Llama a [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de la DE.

   2. Co-crea el DE.

   3. Llamadas [Adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. El DE envía un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al `EVENT_SYNC` SDM con un atributo.

3. El DE envía un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al `EVENT_SYNC` SDM con un atributo.

4. El DE envía un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al `EVENT_SYNC_STOP` SDM con un atributo.

   Separarse de un programa es un proceso simple de dos pasos, de la siguiente manera:

5. Las llamadas SDM [se separan.](../../extensibility/debugger/reference/idebugprogram2-detach.md)

6. La DE envía un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
