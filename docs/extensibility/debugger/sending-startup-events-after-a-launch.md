---
title: Envío de eventos de inicio después de un lanzamiento ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713011"
---
# <a name="send-startup-events-after-a-launch"></a>Enviar eventos de inicio después de un lanzamiento
Una vez que el motor de depuración (DE) se asocia al programa, envía una serie de eventos de inicio de nuevo a la sesión de depuración.

 Los eventos de inicio enviados de vuelta a la sesión de depuración incluyen:

- Un evento de creación de motores.

- Un evento de creación de programas.

- Eventos de creación de subprocesos y carga de módulos.

- Un evento load complete, enviado cuando se carga el código y está listo para ejecutarse, pero antes de que se ejecute cualquier código.

  > [!NOTE]
  > Cuando se continúa con este evento, se inicializan las variables globales y se ejecutan las rutinas de inicio.

- Posibles otros eventos de creación de subprocesos y carga de módulos.

- Un evento de punto de entrada, que indica que el **Main** programa `WinMain`ha alcanzado su punto de entrada principal, como Main o . Normalmente, este evento no se envía si la DE se adjunta a un programa que ya se está ejecutando.

  Mediante programación, el DE primero envía el Administrador de depuración de sesión (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaz, que representa un evento de creación de motor, seguido de un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa un evento de creación de programa.

  Estos eventos suelen ir seguidos de uno o varios eventos de creación de subprocesos [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) y eventos de carga de módulo [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Cuando el código se carga y está listo para ejecutarse, pero antes de que se ejecute cualquier código, el DE envía el SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) carga completa eventos. Por último, si el programa aún no se está ejecutando, la DE envía un evento de punto de entrada [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) lo que indica que el programa ha alcanzado su punto de entrada principal y está listo para la depuración.

## <a name="see-also"></a>Vea también
- [Control de ejecución](../../extensibility/debugger/control-of-execution.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
