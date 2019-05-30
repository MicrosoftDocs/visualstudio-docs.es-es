---
title: Envío de los eventos necesarios | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ef1bb6c436faaefb309ab62db02ee43a0486ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345595"
---
# <a name="send-the-required-events"></a>Enviar los eventos necesarios
Utilice este procedimiento para enviar los eventos necesarios.

## <a name="process-for-sending-required-events"></a>Proceso para el envío de eventos necesarios
 Los eventos siguientes son necesarios, en este orden, cuando el motor de creación de una depuración (DE) y conectarlo a un programa:

1. Enviar una [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto event para el Administrador de depuración de la sesión (SDM) cuando se inicializa la DE uno o más programas en un proceso de depuración.

2. Cuando el programa que se desea depurar se adjunta a, enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto event para el SDM. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

3. Si el programa está asociado a cuando se inicia el proceso, envíe un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto event para el SDM para notificar el IDE del nuevo subproceso. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

4. Enviar una [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objeto event para el SDM cuando el programa que se está depurando se termina de cargar o cuando se completa la asociación al programa. Este evento debe ser un evento de detención.

5. Si se inicia la aplicación que se desea depurar, envíe un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) objeto event para el SDM cuando la primera instrucción de código en la arquitectura en tiempo de ejecución que se va a ejecutar. Este evento siempre es un evento de detención. Cuando a la sesión de depuración, el IDE se detiene en este evento.

> [!NOTE]
> Muchos lenguajes usan inicializadores globales o funciones externas precompiladas (desde la biblioteca de CRT o _Main) al principio de su código. Si el idioma del programa que está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, este código se ejecuta y se envía el evento de punto de entrada cuando el usuario punto de entrada, tales como **principal** o `WinMain`, es se alcanzó.

## <a name="see-also"></a>Vea también
- [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)