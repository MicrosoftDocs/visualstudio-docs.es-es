---
title: Envío de los eventos necesarios | Microsoft Docs
description: Obtenga información sobre los eventos ordenados que son necesarios para crear un motor de depuración y adjuntarlo a un programa en la depuración de Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 49c85e3d371bfd729d55e9d17a6c8de61924e35f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845315"
---
# <a name="send-the-required-events"></a>Enviar los eventos necesarios
Utilice este procedimiento para enviar eventos necesarios.

## <a name="process-for-sending-required-events"></a>Proceso para enviar eventos necesarios
 Los eventos siguientes son necesarios, en este orden, al crear un motor DE depuración (DE) y asociarlo a un programa:

1. Envíe un objeto de evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al administrador de depuración de la sesión (SDM) cuando el de se inicializa para depurar uno o varios programas en un proceso.

2. Cuando el programa que se va a depurar está asociado a, envíe un objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

3. Si el programa está asociado a cuando se inicia el proceso, envíe un objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM para notificar al IDE del nuevo subproceso. Este evento puede ser un evento de detención, dependiendo del diseño del motor.

4. Envíe un objeto de evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM cuando el programa que se está depurando termine de cargarse o cuando se complete la asociación con el programa. Este evento debe ser un evento de detención.

5. Si se inicia la aplicación que se va a depurar, envíe un objeto de evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM cuando la primera instrucción del código de la arquitectura en tiempo de ejecución esté a punto de ejecutarse. Este evento siempre es un evento de detención. Al entrar en la sesión de depuración, el IDE se detiene en este evento.

> [!NOTE]
> Muchos lenguajes utilizan inicializadores globales o funciones externas precompiladas (de la biblioteca CRT o _Main) al principio de su código. Si el idioma del programa que se está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, este código se ejecuta y se envía el evento de punto de entrada cuando se alcanza el punto de entrada del usuario, como **Main** o `WinMain` ,.

## <a name="see-also"></a>Vea también
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
