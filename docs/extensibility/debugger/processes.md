---
title: Procesos de la página de trabajo de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738245"
---
# <a name="processes"></a>Procesos
En la arquitectura del depurador, un *proceso:*

- Es un contenedor para un conjunto de programas. Es muy análogo a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.

- Puede identificarse por nombre, identificador o identificador físico.

- Puede enumerar todos los programas en ejecución (y sus subprocesos).

- Puede describirse a sí mismo, el puerto en el que se ejecuta y la máquina que lo contiene.

- Puede crear uno o más programas, terminar cualquiera de los programas que crea o hacer que un programa se detenga.

- Se representa mediante un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaz, que se crea cuando se inicia el proceso. Un proceso es iniciado por el administrador de depuración de sesión (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  El paquete de depuración puede adjuntar un motor de depuración (DE) a un proceso mediante una llamada a [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), lo que significa que el DE se asocia a todos los programas posibles que se ejecutan en el proceso que puede controlar. Por ejemplo, si Common Language Runtime DE se asocia a un proceso, solo se adjunta a los programas que ejecutan código administrado.

## <a name="see-also"></a>Vea también
- [Programs](../../extensibility/debugger/programs.md)
- [Hilos](../../extensibility/debugger/threads.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Paquete de depuración](../../extensibility/debugger/debug-package.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
