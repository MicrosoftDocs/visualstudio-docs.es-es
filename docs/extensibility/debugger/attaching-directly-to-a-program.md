---
title: Adjuntar directamente a un programa | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio implementa la Asociación de un motor de depuración a un proceso que ya se está ejecutando mediante este procedimiento en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f261d6492943ab0b0da878097685ae2773ddff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055302"
---
# <a name="attach-directly-to-a-program"></a>Adjuntar directamente a un programa
Los usuarios que deseen depurar programas en un proceso que ya se esté ejecutando normalmente siguen este proceso:

1. En el IDE, elija el comando **depurar procesos** en el menú **herramientas** .

    Aparecerá el cuadro de diálogo **Procesos**.

2. Elija un proceso y haga clic en el botón **adjuntar** .

    Aparece el cuadro de diálogo **asociar al proceso** , en el que se enumeran todos los motores de depuración (des) instalados en la máquina.

3. Especifique el DEs que se va a usar para depurar el proceso seleccionado y, a continuación, haga clic en **Aceptar**.

   El paquete de depuración inicia una sesión de depuración y le pasa la lista de DEs. A su vez, la sesión de depuración pasa esta lista, junto con una función de devolución de llamada, al proceso seleccionado y, a continuación, pide al proceso que Enumere los programas que se están ejecutando.

   Mediante programación, en respuesta a la solicitud del usuario, el paquete de depuración crea una instancia del administrador de depuración de la sesión (SDM) y le pasa la lista de DEs seleccionada. Junto con la lista, el paquete de depuración pasa el SDM a una interfaz [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . El paquete de depuración pasa la lista de DEs al proceso seleccionado mediante una llamada a [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Después, el SDM llama a [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) en el puerto para enumerar los programas que se ejecutan en el proceso.

   A partir de este punto, cada motor de depuración se adjunta a un programa exactamente como se detalla en [adjuntar después de un inicio](../../extensibility/debugger/attaching-after-a-launch.md), con dos excepciones.

   Por motivos de eficacia, DEs que se implementa para compartir un espacio de direcciones con el SDM se agrupa de modo que cada DE tenga un conjunto de programas al que se asociará. En este caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) llama a [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) y lo pasa a una matriz de programas que se van a adjuntar.

   La segunda excepción es que los eventos DE inicio que envía un DE adjuntar a un programa que ya se está ejecutando no incluyen normalmente el evento DE punto de entrada.

## <a name="see-also"></a>Consulte también
- [Envío de eventos de inicio después de un inicio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
