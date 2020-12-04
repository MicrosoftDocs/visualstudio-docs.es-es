---
title: Datos adjuntos basados en el inicio | Microsoft Docs
description: Obtenga información sobre los datos adjuntos basados en el inicio de un programa, que es automático y sigue una ruta de acceso como la de los datos adjuntos manuales.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606676"
---
# <a name="launch-based-attachment"></a>Datos adjuntos basados en el inicio
Los datos adjuntos basados en el inicio de un programa son automáticos. Cuando el SDM inicia el proceso que hospeda el programa, los datos adjuntos basados en el inicio siguen una ruta de acceso similar a la del método de datos adjuntos manuales. Para obtener más información, vea [adjuntar al programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proceso de asociación
 La diferencia principal es la secuencia de eventos que siguen a la llamada a **Attach** , como se indica a continuación:

1. Envíe un objeto de evento **IDebugEngineCreateEvent2** al SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).

2. Llame al `IDebugProgram2::GetProgramId` método en la interfaz **IDebugProgram2** que se pasa al método **Attach** .

3. Envíe un objeto de evento **IDebugProgramCreateEvent2** para notificar al SDM que se ha creado el objeto **IDebugProgram2** local para representar el programa en el de.

4. Envíe un objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para notificar al SDM que se crea un nuevo subproceso para el proceso que inició.

## <a name="see-also"></a>Consulte también
- [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)
- [Habilitar la depuración de un programa](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
