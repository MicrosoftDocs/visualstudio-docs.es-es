---
title: Procesos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un proceso en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a707d62443004795824c8bd437c29802635cf41
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606507"
---
# <a name="processes"></a>Procesos
En la arquitectura del depurador, un *proceso*:

- Es un contenedor para un conjunto de programas. Es muy similar a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.

- Puede identificarse por nombre, identificador o identificador físico.

- Puede enumerar todos los programas en ejecución (y sus subprocesos).

- Se puede describir, el puerto en el que se está ejecutando y el equipo que lo contiene.

- Puede crear uno o varios programas, terminar cualquiera de los programas que crea o hacer que se detenga un programa.

- Se representa mediante una interfaz [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , que se crea cuando se inicia el proceso. Un proceso lo inicia el administrador de depuración de sesión (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  El paquete de depuración puede adjuntar un motor de depuración (DE) a un proceso mediante una llamada a [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), lo que significa que el se asocia a todos los programas posibles que se ejecutan en el proceso que puede controlar. Por ejemplo, si el Common Language Runtime DE se asocia a un proceso, solo se adjunta a los programas que ejecutan código administrado.

## <a name="see-also"></a>Consulte también
- [Programs](../../extensibility/debugger/programs.md)
- [Subprocesos](../../extensibility/debugger/threads.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Depurar paquete](../../extensibility/debugger/debug-package.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugprocess2-attach.md)
