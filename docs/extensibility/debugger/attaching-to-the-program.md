---
title: Asociar al programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00b9780d0d302b9e067feed057d1a8d49c5f9fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903223"
---
# <a name="attach-to-the-program"></a>Adjuntar al programa
Una vez que haya registrado los programas con el puerto adecuado, debe adjuntar el depurador al programa que desea depurar.

## <a name="choose-how-to-attach"></a>Elegir cómo adjuntar
 Hay tres formas en las que el administrador de depuración de sesión (SDM) intenta asociarse al programa que se está depurando.

1. En el caso de los programas iniciados por el motor de depuración mediante el método [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (típico de Lenguajes interpretados, por ejemplo), el SDM obtiene la interfaz [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) del objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa al que se va a adjuntar. Si el SDM puede obtener la `IDebugProgramNodeAttach2` interfaz, el SDM llama al método [AutoAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . El `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_OK` para indicar que no se ha adjuntado al programa y que se pueden realizar otros intentos para adjuntar al programa.

2. Si el SDM puede obtener la interfaz [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) del programa al que se está asociando, el SDM llama al método [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . Este enfoque es habitual para los programas que el proveedor del puerto inició de forma remota.

3. Si el programa no se puede adjuntar a través de los `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` métodos o, el SDM carga el motor de depuración (si aún no se ha cargado) llamando a la `CoCreateInstance` función y, a continuación, llama al método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) . Este enfoque es habitual para los programas iniciados localmente por un proveedor de puertos.

    También es posible que un proveedor de Puerto personalizado llame al `IDebugEngine2::Attach` método en la implementación del método del proveedor del puerto personalizado `IDebugProgramEx2::Attach` . Normalmente, en este caso, el proveedor del puerto personalizado inicia el motor de depuración en el equipo remoto.

   Los datos adjuntos se logran cuando el administrador de depuración de sesión (SDM) llama al método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .

   Si ejecuta su DE en el mismo proceso que la aplicación que se va a depurar, debe implementar los métodos siguientes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Después de `IDebugEngine2::Attach` llamar al método, siga estos pasos en su implementación del `IDebugEngine2::Attach` método:

1. Envíe un objeto de evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM. Para obtener más información, consulte [envío de eventos](../../extensibility/debugger/sending-events.md).

2. Llame al método [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se pasó al `IDebugEngine2::Attach` método.

     Esto devuelve un `GUID` que se utiliza para identificar el programa. Se `GUID` debe almacenar en el objeto que representa el programa local en el de, y se debe devolver cuando `IDebugProgram2::GetProgramId` se llama al método en la `IDebugProgram2` interfaz.

    > [!NOTE]
    > Si implementa la `IDebugProgramNodeAttach2` interfaz, se pasa el del programa `GUID` al `IDebugProgramNodeAttach2::OnAttach` método. `GUID`Se utiliza para que el `GUID` método devuelva el programa `IDebugProgram2::GetProgramId` .

3. Envíe un objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para notificar al SDM que el `IDebugProgram2` objeto local se ha creado para representar el programa en el de. Para obtener más información, consulte [envío de eventos](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > No es el mismo `IDebugProgram2` objeto que se pasó al `IDebugEngine2::Attach` método. El objeto que se ha pasado previamente `IDebugProgram2` solo es reconocido por el puerto y es un objeto independiente.

## <a name="see-also"></a>Vea también
- [Datos adjuntos basados en el inicio](../../extensibility/debugger/launch-based-attachment.md)
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md)
