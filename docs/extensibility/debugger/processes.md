---
title: Procesos | Microsoft Docs
description: En este artículo se describe la definición y el rol de un proceso en la arquitectura del depurador en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901258"
---
# <a name="processes"></a>Procesos
En la arquitectura del depurador, un *proceso*:

- Es un contenedor para un conjunto de programas. Es muy análogo a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.

- Puede identificarse por nombre, identificador o identificador físico.

- Puede enumerar todos los programas en ejecución (y sus subprocesos).

- Puede describirse a sí mismo, el puerto en el que se ejecuta y la máquina que lo contiene.

- Puede crear uno o varios programas, finalizar cualquiera de los programas que crea o hacer que un programa se detenga.

- Se representa mediante una [interfaz IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) que se crea cuando se inicia el proceso. El administrador de depuración de sesión (SDM) o [LaunchSuspended inician un proceso.](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

  El paquete de depuración puede asociar un motor de depuración (DE) a un proceso mediante una llamada a [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), lo que significa que de se asocia a todos los programas posibles que se ejecutan en el proceso que puede controlar. Por ejemplo, si Common Language Runtime DE se asocia a un proceso, solo se asocia a programas que ejecutan código administrado.

## <a name="see-also"></a>Consulta también
- [Programs](../../extensibility/debugger/programs.md)
- [Subprocesos](../../extensibility/debugger/threads.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Paquete de depuración](../../extensibility/debugger/debug-package.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugprocess2-attach.md)
