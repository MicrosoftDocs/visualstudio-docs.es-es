---
title: Datos adjuntos basados en el inicio | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738461"
---
# <a name="launch-based-attachment"></a>Datos adjuntos basados en el inicio
Los datos adjuntos basados en el inicio de un programa son automáticos. Cuando el SDM inicia el proceso que hospeda el programa, los datos adjuntos basados en el inicio siguen una ruta de acceso similar a la del método de datos adjuntos manuales. Para obtener más información, vea [adjuntar al programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proceso de asociación
 La diferencia principal es la secuencia de eventos que siguen a la llamada a **Attach** , como se indica a continuación:

1. Envíe un objeto de evento **IDebugEngineCreateEvent2** al SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).

2. Llame al `IDebugProgram2::GetProgramId` método en la interfaz **IDebugProgram2** que se pasa al método **Attach** .

3. Envíe un objeto de evento **IDebugProgramCreateEvent2** para notificar al SDM que se ha creado el objeto **IDebugProgram2** local para representar el programa en el de.

4. Envíe un objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para notificar al SDM que se crea un nuevo subproceso para el proceso que inició.

## <a name="see-also"></a>Vea también
- [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
