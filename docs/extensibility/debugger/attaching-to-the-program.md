---
title: Adjuntar al programa ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739241"
---
# <a name="attach-to-the-program"></a>Adjuntar al programa
Después de registrar los programas con el puerto adecuado, debe adjuntar el depurador al programa que desea depurar.

## <a name="choose-how-to-attach"></a>Elija cómo adjuntar
 Hay tres maneras en que el administrador de depuración de sesión (SDM) intenta asociarse al programa que se está depurando.

1. Para los programas que inicia el motor de depuración a través del método [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (típico de los lenguajes interpretados, por ejemplo), el SDM obtiene la interfaz [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) del objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa al que se adjunta. Si el SDM `IDebugProgramNodeAttach2` puede obtener la interfaz, el SDM entonces llama al método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) El `IDebugProgramNodeAttach2::OnAttach` método `S_OK` vuelve a indicar que no se adjuntó al programa y que se pueden realizar otros intentos para adjuntar al programa.

2. Si el SDM puede obtener el [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfaz desde el programa que se adjunta a, el SDM llama a la [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) método. Este enfoque es típico de los programas que fueron lanzados remotamente por el proveedor del puerto.

3. Si el programa no `IDebugProgramNodeAttach2::OnAttach` se `IDebugProgramEx2::Attach` puede asociar a través de los métodos o, el SDM carga el motor de depuración (si aún no está cargado) llamando a la `CoCreateInstance` función y, a continuación, llama al método [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md) Este enfoque es típico de los programas lanzados localmente por un proveedor portuario.

    También es posible que un proveedor `IDebugEngine2::Attach` de puertos personalizado llame al `IDebugProgramEx2::Attach` método en la implementación del método por parte del proveedor de puertos personalizado. Normalmente, en este caso, el proveedor de puertos personalizado inicia el motor de depuración en el equipo remoto.

   El archivo adjunto se logra cuando el administrador de depuración de sesión (SDM) llama al método [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Si ejecuta la DE en el mismo proceso que la aplicación que se va a depurar, debe implementar los siguientes métodos de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Después `IDebugEngine2::Attach` de llamar al método, siga `IDebugEngine2::Attach` estos pasos en la implementación del método:

1. Enviar un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento al SDM. Para obtener más información, consulte [Envío de eventos](../../extensibility/debugger/sending-events.md).

2. Llame a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que se pasó al `IDebugEngine2::Attach` método.

     Esto devuelve `GUID` un que se utiliza para identificar el programa. Debe `GUID` almacenarse en el objeto que representa el programa local a la `IDebugProgram2::GetProgramId` DE y `IDebugProgram2` debe devolverse cuando se llama al método en la interfaz.

    > [!NOTE]
    > Si implementa `IDebugProgramNodeAttach2` la interfaz, `GUID` el programa `IDebugProgramNodeAttach2::OnAttach` se pasa al método. Esto `GUID` se utiliza para `GUID` el programa `IDebugProgram2::GetProgramId` devuelto por el método.

3. Enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto de evento para `IDebugProgram2` notificar al SDM que el objeto local se creó para representar el programa a la DE. Para obtener más información, consulte [Envío de eventos](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > No es el `IDebugProgram2` mismo objeto que `IDebugEngine2::Attach` se pasó al método. El objeto `IDebugProgram2` pasado anteriormente solo lo reconoce el puerto y es un objeto independiente.

## <a name="see-also"></a>Vea también
- [Archivo adjunto basado en el lanzamiento](../../extensibility/debugger/launch-based-attachment.md)
- [Envío de eventos](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
