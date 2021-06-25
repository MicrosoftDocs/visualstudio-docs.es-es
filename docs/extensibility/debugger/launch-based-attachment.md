---
title: Datos adjuntos basados en inicio | Microsoft Docs
description: Obtenga información sobre los datos adjuntos basados en el inicio de un programa, que es automático y sigue una ruta de acceso como la de los datos adjuntos manuales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97bbc098e766a1025c372ff35c5849bfe652649f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904339"
---
# <a name="launch-based-attachment"></a>Datos adjuntos basados en el inicio
Los datos adjuntos basados en el inicio de un programa son automáticos. Cuando el SDM inicia el proceso que hospeda el programa, los datos adjuntos basados en el inicio siguen una ruta de acceso similar a la del método de datos adjuntos manual. Para obtener información, [vea Asociar al programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>El proceso de asociación
 La principal diferencia es la secuencia de eventos que sigue a **la llamada a Attach,** como se muestra a continuación:

1. Envíe un **objeto de evento IDebugEngineCreateEvent2** al SDM. Para más información, consulte [Envío de eventos](../../extensibility/debugger/sending-events.md).

2. Llame al `IDebugProgram2::GetProgramId` método en la interfaz **IDebugProgram2** pasada al **método Attach.**

3. Envíe un objeto de evento **IDebugProgramCreateEvent2** para notificar al SDM que el objeto **IDebugProgram2** local se creó para representar el programa en el DE.

4. Envíe un [objeto de evento IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para notificar al SDM que se ha creado un nuevo subproceso para el proceso que se inició.

## <a name="see-also"></a>Consulta también
- [Envío de los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)
- [Habilitar un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
