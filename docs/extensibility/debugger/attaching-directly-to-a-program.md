---
title: Adjuntar directamente a un programa ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739252"
---
# <a name="attach-directly-to-a-program"></a>Adjuntar directamente a un programa
Los usuarios que desean depurar programas en un proceso que ya se está ejecutando suelen seguir este proceso:

1. En el IDE, elija el comando **Depurar procesos** del menú **Herramientas.**

    Aparecerá el cuadro de diálogo **Procesos**.

2. Elija un proceso y haga clic en el botón **Adjuntar.**

    Aparece el cuadro de diálogo **Asociar al proceso,** que enumera todos los motores de depuración (DE) instalados en el equipo.

3. Especifique los DE que se utilizarán para depurar el proceso seleccionado y, a continuación, haga clic en **Aceptar**.

   El paquete de depuración inicia una sesión de depuración y le pasa la lista de DE. La sesión de depuración a su vez pasa esta lista, junto con una función de devolución de llamada, al proceso seleccionado y, a continuación, pide al proceso que enumere sus programas en ejecución.

   Mediante programación, en respuesta a la solicitud del usuario, el paquete de depuración crea una instancia del administrador de depuración de sesión (SDM) y le pasa la lista de DE seleccionados. Junto con la lista, el paquete de depuración pasa el SDM un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz. El paquete de depuración pasa la lista de DE al proceso seleccionado llamando a [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). A continuación, el SDM llama [a IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) en el puerto para enumerar los programas que se ejecutan en el proceso.

   A partir de este momento, cada motor de depuración se adjunta a un programa exactamente como se detalla en [Adjuntar después de un lanzamiento,](../../extensibility/debugger/attaching-after-a-launch.md)con dos excepciones.

   Para mayor eficiencia, los DE que se implementan para compartir un espacio de direcciones con el SDM se agrupan de modo que cada DE tenga un conjunto de programas a los que se adjuntará. En este caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) llama a [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) y le pasa una matriz de programas para adjuntar a.

   La segunda excepción es que los eventos de inicio enviados por un DE adjunto a un programa que ya se está ejecutando no suelen incluir el evento de punto de entrada.

## <a name="see-also"></a>Vea también
- [Envío de eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
