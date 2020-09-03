---
title: Envío de eventos de inicio después de un inicio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713011"
---
# <a name="send-startup-events-after-a-launch"></a>Enviar eventos de inicio después de un inicio
Una vez que el motor DE depuración (DE) se adjunta al programa, envía una serie de eventos de inicio de nuevo a la sesión de depuración.

 Los eventos de inicio que se envían de vuelta a la sesión de depuración incluyen:

- Un evento de creación de motor.

- Un evento de creación de programa.

- Creación de subprocesos y eventos de carga de módulos.

- Evento de carga completada que se envía cuando se carga el código y está listo para ejecutarse, pero antes de que se ejecute cualquier código.

  > [!NOTE]
  > Cuando se continúa este evento, se inicializan las variables globales y se ejecutan las rutinas de inicio.

- Otros eventos de creación de subprocesos y carga de módulos.

- Un evento de punto de entrada, que indica que el programa ha alcanzado su punto de entrada principal, como **Main** o `WinMain` . Normalmente, este evento no se envía si el DE se asocia a un programa que ya se está ejecutando.

  Mediante programación, el primero envía el administrador DE depuración DE la sesión (SDM) una interfaz [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , que representa un evento de creación del motor, seguido de un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa un evento de creación del programa.

  Estos eventos suelen ir seguidos de uno o más eventos de creación de subprocesos de [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) y eventos de carga del módulo [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Cuando el código se carga y está listo para ejecutarse, pero antes DE que se ejecute cualquier código, el DE envía al SDM un evento DE carga completa de [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Por último, si el programa no se está ejecutando, el DE envía un evento DE punto DE entrada [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , señalando que el programa ha alcanzado su punto de entrada principal y está listo para la depuración.

## <a name="see-also"></a>Vea también
- [Control de la ejecución](../../extensibility/debugger/control-of-execution.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
