---
title: Asociar al programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6c8aa5d32d579183b0bb42a9152232377423435
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088696"
---
# <a name="attaching-to-the-program"></a>Asociación al programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Después de haber registrado sus programas con el puerto adecuado, debe asociar al depurador al programa que desea depurar.  
  
## <a name="choosing-how-to-attach"></a>Elegir cómo adjuntar  
 Hay tres formas en que el Administrador de depuración de la sesión (SDM) intenta adjuntar al programa que se está depurando.  
  
1. Para los programas que se inician mediante el motor de depuración a través de la [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método (típica de los lenguajes interpretados, por ejemplo), el SDM Obtiene el [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) desde la interfaz el [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa que se va a adjuntar a. Si puede obtener el SDM el `IDebugProgramNodeAttach2` el SDM, a continuación, llama a la interfaz, el [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. El `IDebugProgramNodeAttach2::OnAttach` devuelve del método `S_OK` para indicar que no lo ha adjuntado al programa y que se puede realizar otro intento para adjuntar al programa.  
  
2. Si puede obtener el SDM el [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfaz desde el programa que se asocia a las llamadas SDM el [adjuntar](../../extensibility/debugger/reference/idebugprogramex2-attach.md) método. Este enfoque es típico de programas que se inician de forma remota por el proveedor del puerto.  
  
3. Si el programa no se puede conectar a través de la `IDebugProgramNodeAttach2::OnAttach` o `IDebugProgramEx2::Attach` métodos, el SDM carga el motor de depuración (si aún no está cargada) mediante una llamada a la `CoCreateInstance` función y, a continuación, llama a la [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método. Este enfoque es típico de programas que se inicia localmente por un proveedor de puerto.  
  
    También es posible que un proveedor de puerto personalizado llamar a la `IDebugEngine2::Attach` método de implementación del proveedor de puerto personalizado de la `IDebugProgramEx2::Attach` método. Normalmente, en este caso, el proveedor del puerto personalizado inicia el motor de depuración en el equipo remoto.  
  
   Los datos adjuntos se logra cuando el Administrador de depuración de la sesión (SDM) llama a la [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
   Si ejecuta su DE en el mismo proceso que la aplicación que se desea depurar, a continuación, debe implementar los métodos siguientes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Después de la `IDebugEngine2::Attach` se llama al método, siga estos pasos en la implementación de la `IDebugEngine2::Attach` método:  
  
1. Enviar una [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto event para el SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2. Llame a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que se pasó a la `IDebugEngine2::Attach` método.  
  
     Esto devuelve un `GUID` que se usa para identificar el programa. El `GUID` deben almacenarse en el objeto que representa la variable local del programa a la DE y se debe devolver cuando la `IDebugProgram2::GetProgramId` se llama al método en el `IDebugProgram2` interfaz.  
  
    > [!NOTE]
    >  Si implementa el `IDebugProgramNodeAttach2` interfaz, el programa `GUID` se pasa a la `IDebugProgramNodeAttach2::OnAttach` método. Esto `GUID` se usa para el programa `GUID` devuelto por la `IDebugProgram2::GetProgramId` método.  
  
3. Enviar una [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto de evento para notificar el SDM que local `IDebugProgram2` objeto se creó para representar el programa a la DE. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Esto no es el mismo `IDebugProgram2` objeto que se pasó a la `IDebugEngine2::Attach` método. Anteriormente pasado `IDebugProgram2` objeto es reconocido por el puerto solo y es un objeto independiente.  
  
## <a name="see-also"></a>Vea también  
 [Adjunto basado en Inicio](../../extensibility/debugger/launch-based-attachment.md)   
 [Envío de eventos](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Adjuntar](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md)
