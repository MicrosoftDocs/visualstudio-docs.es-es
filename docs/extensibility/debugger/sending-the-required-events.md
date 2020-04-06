---
title: Envío de los eventos requeridos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712992"
---
# <a name="send-the-required-events"></a>Enviar los eventos requeridos
Use este procedimiento para enviar eventos necesarios.

## <a name="process-for-sending-required-events"></a>Proceso para el envío de eventos requeridos
 Los siguientes eventos son necesarios, en este orden, al crear un motor de depuración (DE) y adjuntarlo a un programa:

1. Envíe un objeto de evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al Administrador de depuración de sesión (SDM) cuando se inicialice la DE para depurar uno o varios programas en un proceso.

2. Cuando se adjunta el programa que se va a depurar, envíe un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto de evento al SDM. Este evento puede ser un evento de parada, dependiendo del diseño del motor.

3. Si el programa está asociado a cuando se inicia el proceso, envíe un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto de evento al SDM para notificar al IDE del nuevo subproceso. Este evento puede ser un evento de parada, dependiendo del diseño del motor.

4. Enviar un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objeto de evento al SDM cuando el programa que se está depurando ha terminado de cargarse o cuando se completa la asociación al programa. Este evento debe ser un evento de detención.

5. Si se inicia la aplicación que se va a depurar, envíe un objeto de evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM cuando se ejecute la primera instrucción de código en la arquitectura en tiempo de ejecución. Este evento siempre es un evento de detención. Al entrar en la sesión de depuración, el IDE se detiene en este evento.

> [!NOTE]
> Muchos lenguajes utilizan inicializadores globales o funciones externas precompiladas (desde la biblioteca DE CRT o _Main) al principio de su código. Si el idioma del programa que está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada **main** inicial, `WinMain`este código se ejecuta y se envía el evento de punto de entrada cuando se alcanza el punto de entrada del usuario, como main o , .

## <a name="see-also"></a>Vea también
- [Habilitación de un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
