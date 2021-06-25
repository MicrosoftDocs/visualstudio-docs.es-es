---
title: Envío de los eventos obligatorios | Microsoft Docs
description: Obtenga información sobre los eventos ordenados necesarios al crear un motor de depuración y adjuntarlo a un programa en Visual Studio depuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b04ca7ed68b975bc68fa509cdc75dc507b9603d6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902272"
---
# <a name="send-the-required-events"></a>Envío de los eventos necesarios
Use este procedimiento para enviar los eventos necesarios.

## <a name="process-for-sending-required-events"></a>Proceso para enviar eventos necesarios
 Los siguientes eventos son necesarios, en este orden, al crear un motor de depuración (DE) y asociarlo a un programa:

1. Envíe un objeto de evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al administrador de depuración de sesión (SDM) cuando se inicialice el DE para depurar uno o varios programas en un proceso.

2. Cuando se adjunta el programa al que se va a depurar, envíe un objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

3. Si el programa está asociado a cuando se inicia el proceso, envíe un objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM para notificar al IDE del nuevo subproceso. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

4. Envíe un objeto de evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM cuando finalice la carga del programa que se está depurando o cuando se complete la asociación al programa. Este evento debe ser un evento de detención.

5. Si se inicia la aplicación que se va a depurar, envíe un objeto de evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM cuando la primera instrucción de código de la arquitectura en tiempo de ejecución esté a punto de ejecutarse. Este evento siempre es un evento de detención. Al depurar paso a paso por pasos la sesión, el IDE se detiene en este evento.

> [!NOTE]
> Muchos lenguajes usan inicializadores globales o funciones externas precompiladas (desde la biblioteca CRT o _Main) al principio de su código. Si el lenguaje del programa que está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, este código se ejecuta y el evento de punto de entrada se envía cuando se alcanza el punto de entrada del usuario, como **main** o `WinMain` .

## <a name="see-also"></a>Consulta también
- [Habilitación de un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
