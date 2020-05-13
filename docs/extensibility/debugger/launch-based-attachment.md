---
title: Adjunto basado en el lanzamiento (Launch-based Attachment) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738461"
---
# <a name="launch-based-attachment"></a>Archivo adjunto basado en el lanzamiento
El archivo adjunto basado en el inicio a un programa es automático. Cuando el SDM inicia el proceso que hospeda el programa, los datos adjuntos basados en el lanzamiento siguen una ruta similar a la del método de datos adjuntos manual. Para obtener más información, consulte [Adjuntar al programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>El proceso de fijación
 La principal diferencia es la secuencia de eventos que siguen a la llamada **Attach,** como se indica a continuación:

1. Enviar un **IDebugEngineCreateEvent2** objeto de evento al SDM. Para obtener más información, consulte [Enviar eventos](../../extensibility/debugger/sending-events.md).

2. Llame `IDebugProgram2::GetProgramId` al método en el **IDebugProgram2** interfaz pasada a la **Attach** método.

3. Enviar un **IDebugProgramCreateEvent2** objeto de evento para notificar al SDM que el local **IDebugProgram2** objeto se creó para representar el programa a la DE.

4. Enviar un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto de evento para notificar al SDM que se crea un nuevo subproceso para el proceso que se inició.

## <a name="see-also"></a>Vea también
- [Enviar los eventos requeridos](../../extensibility/debugger/sending-the-required-events.md)
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
