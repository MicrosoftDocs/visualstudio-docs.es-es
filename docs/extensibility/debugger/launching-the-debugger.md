---
title: Lanzamiento del depurador ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738448"
---
# <a name="launch-the-debugger"></a>Inicie el depurador
Para iniciar el depurador es necesario enviar la secuencia correcta de métodos y eventos con sus atributos adecuados.

## <a name="sequences-of-methods-and-events"></a>Secuencias de métodos y eventos

1. Se llama al administrador de depuración de sesión (SDM) eligiendo el menú **Depurar** y, a continuación, seleccionando **Iniciar**. Para obtener más información, consulte [Iniciar un programa](../../extensibility/debugger/launching-a-program.md).

2. El SDM llama al método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. En función del modelo de proceso `IDebugProgramNodeAttach2::OnAttach` del motor de depuración (DE), el método devuelve uno de los métodos siguientes, que determina lo que sucede a continuación.

     Si `S_FALSE` se devuelve, el motor de depuración (DE) se cargará en el proceso de la máquina virtual.

     o bien

     Si `S_OK` devuelve, el DE se cargará en proceso del SDM. A continuación, el SDM realiza las siguientes tareas:

    1. Llama a [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de la DE.

    2. Co-crea el DE.

    3. Llamadas [Adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. El DE envía un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al `EVENT_SYNC` SDM con un atributo.

5. El DE envía un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al `EVENT_SYNC` SDM con un atributo.

6. El DE envía un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al `EVENT_SYNC` SDM con un atributo.

7. El DE envía un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al `EVENT_SYNC` SDM con un atributo.

8. El DE envía un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al `EVENT_SYNC` SDM con un atributo.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
- [Lanzamiento de un programa](../../extensibility/debugger/launching-a-program.md)
