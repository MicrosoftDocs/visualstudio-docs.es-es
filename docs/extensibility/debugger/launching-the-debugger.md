---
title: Iniciar el depurador | Microsoft Docs
description: Obtenga información sobre la secuencia de métodos y eventos con los atributos adecuados necesarios para iniciar el depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9f8bc85672fc89205ab25fa9954e1c28e10f859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926395"
---
# <a name="launch-the-debugger"></a>Inicio del depurador
Iniciar el depurador requiere el envío de la secuencia correcta de métodos y eventos con sus atributos adecuados.

## <a name="sequences-of-methods-and-events"></a>Secuencias de métodos y eventos

1. Se llama al administrador de depuración de sesión (SDM) eligiendo el menú **depurar** y, a continuación, eligiendo **iniciar**. Para obtener más información, vea [iniciar un programa](../../extensibility/debugger/launching-a-program.md).

2. El SDM llama al método [AutoAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

3. Según el modelo de proceso del motor DE depuración (DE), el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los siguientes métodos, que determina lo que ocurre a continuación.

     Si `S_FALSE` devuelve, el motor de depuración (de) se cargará en el proceso de la máquina virtual.

     o bien

     Si `S_OK` devuelve, el de se cargará en proceso del SDM. Después, el SDM realiza las siguientes tareas:

    1. Llama a [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de de.

    2. Crea el DE.

    3. Llama a [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. El DE envía un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM con un `EVENT_SYNC` atributo.

5. El DE envía un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM con un `EVENT_SYNC` atributo.

6. El DE envía un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM con un `EVENT_SYNC` atributo.

7. El DE envía un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM con un `EVENT_SYNC` atributo.

8. El DE envía un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM con un `EVENT_SYNC` atributo.

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
- [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)
